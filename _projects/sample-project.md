---
title: Serverless ETL for Marketing Events
date: 2025-08-15
excerpt: "Real-time ETL with Lambda + Kinesis + Athena under $50/month."
image: /assets/img/project-default.jpg
stack: [AWS Lambda, Kinesis, Glue, Athena, S3]
links:
  - label: Source (private)
    url: "#"
  - label: Case study
    url: "/projects/sample-project/"
---

**Context:** The client needed to centralize clickstream data and power near‑real‑time dashboards without a pricey vendor.

**Solution:** We built a serverless ingestion pipeline with Kinesis → Lambda → S3 (partitioned by date) and queried with Athena. Glue crawlers maintained the catalog.
