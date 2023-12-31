---
layout: post
title: "Lessons from Sectigo's Expired Certificates"
date:  2020-05-30 20:43:52
categories: ssl
tags: ssl issues sectigo certificates ssl-expiry
image: /assets/article_images/2020-05-30-fix-sectigo-expired-cert/ssl.JPG
---

## Lessons from Sectigo's Expired Certificates - Why it is important to validate SSL certificate chain and not just root SSL certificate in monitoring systems
<br />

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

### How did we fix it?
The fix was to update our full certificate file with the new roots. In our case, it looked like the following -

```
1. Subject CN: *.ourdomain.com > Issuer CN: Sectigo RSA Domain Validation Secure Server CA
2. Subject CN: Sectigo RSA Domain Validation Secure Server CA > Issuer CN: USERTrust RSA Certification Authority
3. Subject CN: USERTrust RSA Certification Authority > Issuer CN: AddTrust External CA Root
4. Subject CN: AddTrust External CA Root > Issuer CN: AddTrust External CA Root
```

We updated the new UserTrust certs for Sectigo from [this link](https://support.sectigo.com/articles/Knowledge/Sectigo-AddTrust-External-CA-Root-Expiring-May-30-2020).

The modern root certificates are availble under the heading **USERTrust RSA Certification Authority**. A couple of sections below the cross certificates are also availble.

The certificates need not be re-issued and can be updated with these new ones. In our case 3 and 4 in the full chain were replaced.

Hope this helps someone. Let me know in case there is some correction.


