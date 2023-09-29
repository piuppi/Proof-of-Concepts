# Vulnerabilities found in 'BIG-IP Edge Client for Windows and MacOS' (https://www.f5.com)

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)

### Security Advisory

* #### [CVE-2023-36858](https://nvd.nist.gov/vuln/detail/CVE-2023-36858) - BIG-IP Edge Client for Windows and MacOS vulnerability
  https://my.f5.com/manage/s/article/K000132563

  An insufficient verification of data vulnerability exists in BIG-IP Edge Client for Windows and macOS that may allow an attacker to modify its configured server list.
  ##### Impact
  An authenticated attacker with local access to the BIG-IP Edge Client on a Windows or macOS system may modify the BIG-IP Edge Client's server list and direct traffic to a malicious system.

* #### [CVE-2023-24461](https://nvd.nist.gov/vuln/detail/CVE-2023-24461) - BIG-IP Edge Client for Windows and MacOS vulnerability
  https://my.f5.com/manage/s/article/K000132539

  An improper certificate validation vulnerability exists in the BIG-IP Edge Client for Windows and macOS and may allow an attacker to impersonate a BIG-IP APM system.
  ##### Impact
  An unauthenticated attacker with a man in the middle position may exploit this vulnerability and trick the BIG-IP Edge Client to establish connections with an illegitimate BIG-IP APM system.


* #### [CVE-2023-22372](https://nvd.nist.gov/vuln/detail/CVE-2023-22372) - BIG-IP Edge Client for Windows and MacOS vulnerability
  https://my.f5.com/manage/s/article/K000132522

  In the pre connection stage, an improper enforcement of message integrity vulnerability exists in BIG-IP Edge Client for Windows and Mac OS.
  ##### Impact
  An unauthenticated attacker with a man in the middle position may exploit this vulnerability to modify requests and responses to and from the BIG-IP Edge Client.
