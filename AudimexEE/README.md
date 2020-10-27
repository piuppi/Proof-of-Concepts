# Vulnerabilities discovered in AudimexEE ver 14.1.0 (https://www.web-audimex.com)
***
### Overview
AudimexEE is an audit software solution for large enterprises that fulfils highest demands in terms of the implementation of auditing processes and corporate structures surrounding a powerful and highly flexible audit universe.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) from [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)

### Proof of concept (POC)

#### Before **14.1.1** version is vulnerable to **SQL Injection**. An attacker with limited privileges (auditor profile) can achieve a SQL injection that can lead in data leakage.
- Link to **[SQL Injection](SQLInjection.md)**

#### Before **14.1.1** version is vulnerable to Reflected XSS (Cross-Site-Scripting)*, allows remote attackers to inject arbitrary web script or HTML via '**action, cargo and panel**' parameters, that can lead in data leakage.
- Link to **[Reflected XSS](Reflected-XSS.md)**
