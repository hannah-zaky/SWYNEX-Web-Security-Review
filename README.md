# SWYNEX-Web-Security-Review

Defensive web security review performed as part of Task 3 of the SWYNEX Technologies internship.

## Overview

This repository documents a manual security assessment of [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/), an intentionally vulnerable training application, run locally in Docker and tested with Burp Suite Community Edition.

**Scope:** Local Docker instance only, bound to `127.0.0.1:3000`. No third-party or production systems were tested.

## Environment

- **OS:** Kali Linux
- **Target:** OWASP Juice Shop (`bkimminich/juice-shop`)
- **Setup command:**
  ```bash
  docker run -d --name juiceshop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
  ```
- **Tooling:** Burp Suite Community Edition (Proxy + Repeater)

## Findings Summary

| # | Finding | Severity |
|---|---------|----------|
| 1 | SQL Injection — login bypass | Critical |
| 2 | Broken Access Control (IDOR) — basket enumeration | High |
| 3 | Sensitive Data Exposure — public `/ftp` directory | High |
| 4 | DOM-based XSS — search field | Medium |
| 5 | Security Misconfiguration — missing headers / permissive CORS | Low/Medium |

Full details, reproduction steps, and remediation recommendations for each finding are in [`report.docx`](./report.docx).

## Repository Structure

```
SWYNEX-Web-Security-Review/
├── README.md
├── report.docx
└── screenshots/
    ├── sqli_repeater_request_response.png
    ├── admin_panel.png
    ├── idor_repeater_edited.png
    ├── idor_repeater.png
    ├── ftp_listing.png
    ├── xss_input.png
    ├── xss_alert.png
    └── missing_headers.png
```

## Disclaimer

All testing was performed exclusively against a local, intentionally vulnerable training application running on `127.0.0.1`. No external, third-party, or production systems were accessed or tested.
