
# Vulnerabilities discovered in Knowage Suite ver 7.1

### Overview
Knowage ([https://www.knowage-suite.com](https://www.knowage-suite.com)) is the Open Source Business Analytics Suite combining traditional and big data sources into valuable and meaningful information.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
#### [Antonio Scibilia](https://www.linkedin.com/in/nynuz/) of [Cybertech S.r.l.](https://cybertech.eu)
 
### Proof of concept (POC)

#### SQL Injection vulnerability found in Knowage Suite version 7.1 in the analytics driver component when running a report.

- Go to **[PoC](SQLi-KnowageSuite.md)**

#### Knowage Suite before 7.4 is vulnerable to Reflected XSS (Cross-Site-Scripting). An attacker can inject arbitrary web script in /restful-services/publish' via the 'EXEC_FROM' parameter that can lead to data leakage.

- Go to **[PoC](XSS-KnowageSuite.md)**

#### Stored HTML Injection vulnerability found in Knowage Suite version 7.1. An attacker can inject arbitrary HTML in "/restful-services/2.0/analyticalDrivers" via the 'LABEL' and 'NAME' parameters.

- Go to **[PoC](HTLM-Injection-KnowageSuite.md)**

### Timeline
- **2021-02-09**: Discovered and reported to [Knowage](https://www.knowage-suite.com)
- **2021-02-09**: Got instant response from Knowage development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback."
- **2021-03-22**: Knowage Team fixed this issue in Knowage version 7.4.
- **2021-03-30**: We have requested the CVE-ID to the MITRE
