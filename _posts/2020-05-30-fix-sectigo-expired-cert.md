---
layout: post
title: "Sectigo Certificate Expired? Root Cause & Fixes"
description: "Debug Sectigo/TLS outages: broken chains, why some clients fail, fast server fixes, and proactive monitoring to prevent the next expiry incident."
tags: [TLS, SSL, Certificates, Sectigo, PKI, Security, Monitoring]
categories: [ tech ]
permalink: /2020-05-30-fix-sectigo-expired-cert
author: "Arun"
---

# Sectigo Certificate Expired? Root Cause, Fixes, and Monitoring

Seeing **SSL/TLS errors** after a **Sectigo certificate expired**? The root cause is often a **broken chain**—your server is serving an outdated intermediate while your leaf cert remains valid. Here’s how expiry ripples through clients, how to patch servers fast, and how to monitor so it doesn’t happen again. This ‘Sectigo certificate expired’ incidents trace back to a mismatched SSL chain served by the web server.

## What actually expired

### How it all started today?
Today we noticed that in some of our applications connection to our internal API's are failing with the following error messages -
```
RestClient::SSLCertificateNotVerified (SSL_connect returned=1 errno=0 state=error: certificate verify failed)
```

When we checked the nginx logs of the API's we saw the following error - 
```
SSL_shutdown() failed (SSL: error:140E0197:SSL routines:SSL_shutdown:shutdown while in init) while SSL handshaking
```

API's health check from browser did not show any issue, all seemed fine. Infact, the SSL certificate was not expiring before 2021. So what was causing this issue? Upon further investigation it was found that one of the intermediate certificate in the certificate chain has expired!
Sectigo's External CA root expired and thus our certifactes had issues.

## why chains matter 

- A chain problem can break strict clients (WAFs, firewalls, Java apps) even when modern browsers appear fine.
- Browsers may fetch alternative chains automatically; network devices typically won’t.
- The practical fix: **install the correct intermediate bundle** and verify end‑to‑end.

## Why some clients fail while others keep working

- **Servers can ship different chains.** If your bundle includes an obsolete intermediate, strict clients fail path validation.
- **Path building differs per client.** Some validate only what the server presents; others attempt alternate paths.
- **Caches & truststores**: devices or apps may pin old chains or cache them for long periods.

## Fast fix (copy‑paste runbook)

### 1) Inspect the served chain
```bash
echo | openssl s_client -connect example.com:443 -servername example.com -showcerts 2>/dev/null | openssl x509 -noout -issuer -subject -enddate
```
- Confirm the **issuer** and **enddate** for each cert; look for expired intermediates.

### 2) Install the correct intermediate bundle
- Download the current Sectigo intermediate for your leaf certificate family.
- Update your web server’s chain:
  - **Nginx:** concatenate leaf + intermediate(s) in the chain file you reference.
  - **Apache:** use `SSLCertificateFile` for leaf and `SSLCertificateChainFile` (or bundle) for intermediates.
- Reload gracefully and verify again.

### 3) Clear stale caches
- Restart downstream proxies/load balancers that cache certificate chains.
- For Java applications, update any manually imported truststores.

### 4) Re‑verify the connection
```bash
openssl s_client -connect example.com:443 -servername example.com -verify_return_error
```
- Expect `verify return code: 0 (ok)`.

## Proactive monitoring that catches chain failures

- **Synthetic checks** for both **leaf and intermediate** expiries (30/15/7‑day thresholds).
- Assert the **expected issuer fingerprint** so mismatched chains alert you early.
- Test from multiple client types: a **headless browser** and a **strict OpenSSL/Java** client.
- Add dashboards with **Days to Expiry** for leaf vs chain side by side.

## Hardening issuance and renewals

- Automate renewals (ACME/Certbot for public endpoints; private PKI for internal).
- Keep an internal “**bundle source of truth**” with fingerprints and download URLs.
- For CDNs/WAFs, plan rotation windows and validate in a pre‑prod distribution.

## FAQ

**Why does Chrome work but my firewall says “expired”?**  
Your server likely shipped an outdated intermediate. Browsers may find a newer path; the firewall uses what you served. Install the correct bundle and retest.

**Should I rely on dynamic AIA fetching?**  
Treat it as a safety net, not a guarantee. Always bundle the correct chain on the server.

**How often do I need to renew?**  
Public TLS lifespans are short; automate renewals and alert well ahead of expiry.

## Conclusion

Treat certificate **chains** as first‑class confg. To avoid the next ‘Sectigo certificate expired’ page, monitor both leaf and chain expiries and verify the served bundle.
