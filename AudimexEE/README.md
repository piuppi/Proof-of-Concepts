# Vulnerabilities discovered in AudimexEE ver 14.1.0

### Overview
AudimexEE ([https://www.web-audimex.com/audimexee](https://www.web-audimex.com/audimexee)) is an audit software solution for large enterprises that fulfils highest demands in terms of the implementation of auditing processes and corporate structures surrounding a powerful and highly flexible audit universe.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
 
### Proof of concept (POC)

#### AudimexEE versions prior to 14.1.1 are vulnerable to SQL Injection. An attacker with limited privileges (auditor profile) can perform a SQL injection via the 'object_path' parameter, using a payload to trigger an 'error-based' or 'boolean-based blind', that can lead to data leakage.

- Go to **[CVE-2020-28115](SQLInjection.md)**

#### AudimexEE versions prior to 14.1.1 are vulnerable to Reflected XSS (Cross-Site-Scripting) if you don't set the recommended security configuration parameter "unique_error_numbers". This vulnerability allows remote attackers to inject arbitrary web scripts or HTML via the 'action, cargo and panel' parameters, that can lead to data leakage.

- Go to **[CVE-2020-28047](Reflected-XSS.md)**

### Timeline
- **2020-10-09**: Discovered and reported to [Audimex](https://www.web-audimex.com)
- **2020-10-09**: Got instant response from Audimex development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback."
- **2020-10-12**: Audimex fixed this issue in audimexEE version 14.1.1
- **2020-11-05**: I have obtained the CVE IDs and published the PoC
