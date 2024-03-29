
# CVE-2020-28047: AudimexEE before 14.1.1 is vulnerable to Reflected XSS (Cross-Site-Scripting). If the recommended security configuration parameter "unique_error_numbers" is not set, remote attackers can inject arbitrary web script or HTML via 'action, cargo, panel' parameters that can lead to data leakage.

### Overview

AudimexEE (https://www.web-audimex.com) is an audit software solution for large enterprises that fulfils highest demands in terms of the implementation of auditing processes and corporate structures surrounding a powerful and highly flexible audit universe.

### Description
Reflected cross-site scripting vulnerabilities arise when data is copied from a request and echoed into the application's immediate response in an unsafe way. The vulnerability is present in the wal.fcgi, can be exploited* via POST request on '**action, cargo and panel**' parameters, using a payload to trigger the HTML Tag. However it was possible to convert the request to use the GET method.
  
#### * Important Note: the XSS does not occur when setting the recommended security configuration parameter "**unique_error_numbers**".

### Impact
An attacker can use the vulnerability to construct a request that, if issued by another application user, will cause JavaScript code supplied by the attacker to be executed within his browser in his session context of the application. The attacker-supplied code can perform a wide variety of actions, such as performing arbitrary actions on victim's behalf, and logging their keystrokes. Users can be induced to initiate the attacker's crafted request in various ways. For example, the attacker could send a victim a link containing a malicious URL via email or instant message.

### Timeline
- **2020-10-09**: Discovered and reported to [Audimex](https://www.web-audimex.com)
- **2020-10-09**: Got instant response from Audimex development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback."
- **2020-10-12**: Audimex fixed this issue in audimexEE version 14.1.1
- **2020-11-05**: I have obtained the [CVE-2020-28047](https://nvd.nist.gov/vuln/detail/CVE-2020-28047) and published the PoC

### Discovered by

#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)

### Proof of concept (POC)
#### Reproducing Steps

After authenticating on the **AudimexEE v.14** portal with an **'any'** profile,

![Screenshot](images/audimex.jpg)


I have identified a **Reflected XSS (Cross-Site-Scripting)** in the main section of the site wal.fcgi

![Screenshot](images/xss-menu.jpg)

All contextual menu requests that contain references to this parameters are vulnerable to HTML/javascript code injection. This flaw triggers an application error that does not properly sanitize HTML/Javascript tags, below the evidence.


##### Request:

![Screenshot](images/xss-request.jpg)



##### Response:

![Screenshot](images/xss-response.jpg)

##### Render page:
![Screenshot](images/xss-render.jpg)


### Suggestions

In most situations where user-controllable data is copied into application responses, cross-site scripting attacks can be prevented using two layers of defenses:
- Input should be validated as strictly as possible on arrival, given the kind of content that it is expected to contain. For example, personal names should consist of alphabetical and a small range of typographical characters, and be relatively short; a year of birth should consist of exactly four numerals; email addresses should match a well-defined regular expression. Input which fails the validation should be rejected, not sanitized.
- User input should be HTML-encoded at any point where it is copied into application responses. All HTML metacharacters, including < > " ' and =, should be replaced with the corresponding HTML entities (&lt; &gt; etc).
In cases where the application's functionality allows users to author content using a restricted subset of HTML tags and attributes (for example, blog comments which allow limited formatting and linking), it is necessary to parse the supplied HTML to validate that it does not use any dangerous syntax; this is a non-trivial task.




