# Sentinel — Enterprise Threat Modeling Technical Notes

**Author:** Uzair Ali  
**Task:** Enterprise Threat Modeling Framework & Incident Response Blueprint  
**Assessment type:** Hypothetical design exercise

## 1. Objective and scope
The project presents an interactive dashboard for modeling threats in a hypothetical enterprise environment. The reference system includes employee endpoints, remote access, an identity provider, a firewall/WAF, a business application, file/data storage, centralized logging, and protected backups. No real systems were scanned or accessed.

## 2. Architecture and trust boundaries
External users and the internet are treated as untrusted. A firewall/WAF filters inbound traffic. The identity provider verifies identity and applies MFA and conditional access. The application and data layer should be segmented, with access granted by role and business need. Centralized logging provides monitoring and investigation evidence. Backups should be access-controlled, isolated from ordinary administrative paths, and tested.

The diagram is conceptual and not a deployment specification. Actual network routes, data flows, protocols, data classifications, and system owners must be documented during a real assessment.

## 3. STRIDE threat register

| Category | Example scenario | Impact | Recommended controls |
|---|---|---|---|
| Spoofing | Stolen employee credentials are reused | Unauthorized access | MFA, conditional access, phishing-resistant authentication, sign-in alerts |
| Tampering | Sensitive records are modified without authorization | Integrity loss | Least privilege, versioning, integrity monitoring, protected backups |
| Repudiation | A sensitive action cannot be reliably attributed | Investigation gaps | Centralized, time-synchronized, tamper-resistant audit logs |
| Information Disclosure | Over-permissive sharing exposes confidential files | Privacy and business harm | Access reviews, encryption, data classification, download monitoring |
| Denial of Service | Malicious request volume disrupts an application | Service unavailability | Rate limiting, WAF, monitoring, continuity planning |
| Elevation of Privilege | Standard account gains administrative rights | Wider compromise | Patch management, privileged access controls, separation of duties |

## 4. Qualitative risk prioritization
Initial example priorities:
- **High:** compromised employee account; unauthorized data modification; confidential data exposure; privileged-account abuse.
- **Medium:** application service disruption.
These ratings are illustrative estimates only. A real risk assessment should score likelihood and impact using evidence, asset criticality, threat intelligence, existing controls, and business context.

## 5. Zero Trust control design
1. **Verify explicitly:** MFA, strong authentication, device posture, and conditional access.
2. **Apply least privilege:** role-based access, just-in-time elevation where possible, separate administrative accounts, and periodic access reviews.
3. **Assume breach:** segment networks, monitor endpoint and identity activity, and restrict lateral movement.
4. **Protect data:** encryption in transit and at rest, data classification, controlled sharing, and tested protected backups.
5. **Improve visibility:** centralize identity, endpoint, server, firewall, and application logs; alert on anomalous sign-ins, privilege changes, and unusual data access.

## 6. Incident response blueprint

### Stage 1 — Preparation
Define roles and escalation paths, maintain asset inventories, enable logging and endpoint protection, maintain tested backups, and rehearse ransomware and data-exposure scenarios.

### Stage 2 — Detection and analysis
Validate alerts, identify affected users and hosts, correlate endpoint and identity logs, preserve evidence, record timestamps, classify severity, and determine the likely scope.

### Stage 3 — Containment, eradication, and recovery
Coordinate containment with incident leadership; isolate affected systems or revoke sessions where appropriate; reset compromised credentials; preserve evidence; remediate the root cause; restore from verified clean backups; patch and monitor before normal operations resume.

### Stage 4 — Post-incident activities
Document a timeline and impact, coordinate required notifications with authorized legal/privacy teams, run a lessons-learned review, assign corrective actions, and update controls and playbooks.

## 7. Validation and limitations
This prototype is static and illustrative. It does not integrate with a SIEM, scan endpoints, validate an organization's identity configuration, or carry out response actions. No live security testing has been performed. Recommendations must be validated against real architecture, policies, legal obligations, and operational requirements before use.

## 8. Conclusion
The dashboard translates STRIDE into a practical threat register and connects identified risks to Zero Trust controls and incident response steps. It is a starting point for discussion and planning, not a substitute for a system-specific threat assessment.
