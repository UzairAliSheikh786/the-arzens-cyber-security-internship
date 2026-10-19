# Sentinel — Enterprise Threat Modeling Dashboard

**Author:** Uzair Ali  
**Project:** Cybersecurity Internship — Task 4  
**Stack:** HTML, CSS, Vanilla JavaScript (no external dependencies)

## Overview
Sentinel is a responsive, interactive educational dashboard for a hypothetical enterprise. It demonstrates:
- A conceptual enterprise security architecture and trust boundaries
- STRIDE threat categories with interactive category and severity filters
- A qualitative risk register
- Zero Trust security principles and baseline controls
- A four-stage incident response playbook with selectable stage details

## Run locally
1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. No package installation, build step, server, or internet connection is required.

## Project structure
- `index.html` — complete dashboard, styles, and interactions
- `THREAT_MODEL.md` — supporting technical documentation and assumptions

## Limitations and responsible use
This is a static educational design prototype. It does not connect to a SIEM, scan hosts, authenticate users, or execute incident response actions. Threat scenarios and risk ratings are illustrative, not results from a real assessment. Validate all controls against the actual environment before operational use.

## Key concepts
- **STRIDE:** Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege
- **Zero Trust:** Explicit verification, least privilege, and assume breach
- **Incident response:** Preparation; detection and analysis; containment/eradication/recovery; post-incident activities
