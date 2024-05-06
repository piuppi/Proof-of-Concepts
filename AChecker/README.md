# Vulnerabilities discovered in AChecker 1.5

### Overview
AChecker (https://github.com/inclusive-design/AChecker) is an automated Web Accessibility Checker tool developed by the Inclusive Design Institute. It is used to evaluate the accessibility of HTML pages and ensure they can be accessed by all individuals, including those with disabilities who use assistive technologies to navigate the Internet.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
 
### Proof of concept (POC)

#### AChecker 1.5 allows remote attackers to read the contents of arbitrary files via the download.php 'path' parameter by using Unauthenticated Path Traversal. This occurs through readfile in PHP.
<br>***NOTE**: This vulnerability only affects products that are no longer supported by the maintainer.*

- Go to PoC:     **[CVE-2024-34523](CVE-2024-34523.md)**
- Go to Exploit: **[CVE-2024-34523.py](CVE-2024-34523.py)**
