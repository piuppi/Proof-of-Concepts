
# Vulnerabilities discovered in Knowage Suite ver 7.1

### Overview
Knowage ([https://www.knowage-suite.com](https://www.knowage-suite.com)) is the Open Source Business Analytics Suite combining traditional and big data sources into valuable and meaningful information.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
#### [Antonio Scibilia](https://www.linkedin.com/in/nynuz/) of [Cybertech S.r.l.](https://cybertech.eu)
 
### Proof of concept (POC)

#### CVE-2021-30055 : A SQL injection vulnerability in Knowage Suite version 7.1 exists in the documentexecution/url analytics driver component via the 'par_year' parameter when running a report.

- Go to **[CVE-2021-30055](SQLi-KnowageSuite.md)**

#### CVE-2021-30056 : Knowage Suite before 7.4 is vulnerable to reflected cross-site scripting (XSS). An attacker can inject arbitrary web script in /restful-services/publish via the 'EXEC_FROM' parameter that can lead to data leakage.

- Go to **[CVE-2021-30056](XSS-KnowageSuite.md)**

#### CVE-2021-30057 : A stored HTML injection vulnerability exists in Knowage Suite version 7.1. An attacker can inject arbitrary HTML in "/restful-services/2.0/analyticalDrivers" via the 'LABEL' and 'NAME' parameters.

- Go to **[CVE-2021-30057](HTLM-Injection-KnowageSuite.md)**

#### CVE-2021-30058 : Knowage Suite before 7.4 is vulnerable to cross-site scripting (XSS). An attacker can inject arbitrary external script in '/knowagecockpitengine/api/1.0/pages/execute' via the 'SBI_HOST' parameter.

- Go to **[CVE-2021-30058](XSSI-KnowageSuite.md)**

#### CVE-2021-30211 : Knowage Suite 7.3 is vulnerable to Stored Cross-Site Scripting (XSS). An attacker can inject arbitrary web script in '/knowage/restful-services/signup/update' via the 'surname' parameter.

- Go to **[CVE-2021-30211](Stored-XSS-KnowageSuite7-3-surname.md)**

#### CVE-2021-30212 : Knowage Suite 7.3 is vulnerable to Stored Cross-Site Scripting (XSS). An attacker can inject arbitrary web script in '/knowage/restful-services/documentnotes/saveNote' via the 'nota' parameter.

- Go to **[CVE-2021-30212](Stored-XSS-KnowageSuite7-3-notes.md)**

#### CVE-2021-30213 : Knowage Suite 7.3 is vulnerable to unauthenticated reflected cross-site scripting (XSS). An attacker can inject arbitrary web script in '/servlet/AdapterHTTP' via the 'targetService' parameter.

- Go to **[CVE-2021-30213](XSS-KnowageSuite7-3_unauth.md)**

#### CVE-2021-30214 : Knowage Suite 7.3 is vulnerable to Stored Client-Side Template Injection in '/knowage/restful-services/signup/update' via the 'name' parameter.

- Go to **[CVE-2021-30214](CSTI-KnowageSuite7-3.md)**

### Timeline
- **2021-02-09**: Discovered and reported to [Knowage](https://www.knowage-suite.com)
- **2021-02-09**: Got instant response from Knowage development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback."
- **2021-03-22**: Knowage Team fixed this issue in Knowage version 7.4.
