
# Knowage Suite before 7.4 is vulnerable to Reflected XSS (Cross-Site-Scripting). An attacker can inject arbitrary web script in /restful-services/publish' via the 'EXEC_FROM' parameter that can lead to data leakage.

### Overview

Knowage ([https://www.knowage-suite.com](https://www.knowage-suite.com)) is the Open Source Business Analytics Suite combining traditional and big data sources into valuable and meaningful information.

### Description
The vulnerability is present in the '**/restful-services/publish**', and can be exploited throuth a GET request via the '**EXEC_FROM**' parameter.
  
### Impact
An attacker can use the vulnerability to construct a request that, if issued by another application user, will cause JavaScript code supplied by the attacker to be executed within his browser in his session context of the application. The attacker-supplied code can perform a wide variety of actions, such as performing arbitrary actions on victim's behalf, and logging their keystrokes. Users can be induced to initiate the attacker's crafted request in various ways. For example, the attacker could send a victim a link containing a malicious URL via email or instant message.

### Timeline
- **2021-02-09**: Discovered and reported to [Knowage](https://www.knowage-suite.com)
- **2021-02-09**: Got instant response from Knowage development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback.
- **2021-03-22**: Knowage Team fixed this issue in Knowage version 7.4.0
- **2021-03-30**: We have requested the CVE-ID to the MITRE

### Discovered by

#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
#### [Antonio Scibilia](https://www.linkedin.com/in/nynuz/) of [Cybertech S.r.l.](https://cybertech.eu)


### Proof of concept (POC)
#### Reproducing Steps

After authenticating on the **Knowage Suite** portal with an any profile, Just navigate to any contextual menu on the site and intercept the GET request, which will contain the '**EXEC_FROM**' parameter.

In practice, all context menu requests that contain references to this parameter are vulnerable to HTML/javascript injection.

So, if you append an XSS payload to the 'EXEC_FROM' parameter, this is reflected in the HTML DOM of the page that does not properly sanitise user input.

##### Request:

![Screenshot](images/xss-execfrom.png)

##### Response:

![Screenshot](images/xss-execfrom-alert.png)

### Suggestions

In most situations where user-controllable data is copied into application responses, cross-site scripting attacks can be prevented using two layers of defenses:
- Input should be validated as strictly as possible on arrival, given the kind of content that it is expected to contain. For example, personal names should consist of alphabetical and a small range of typographical characters, and be relatively short; a year of birth should consist of exactly four numerals; email addresses should match a well-defined regular expression. Input which fails the validation should be rejected, not sanitized.
- User input should be HTML-encoded at any point where it is copied into application responses. All HTML metacharacters, including < > " ' and =, should be replaced with the corresponding HTML entities (&lt; &gt; etc).
In cases where the application's functionality allows users to author content using a restricted subset of HTML tags and attributes (for example, blog comments which allow limited formatting and linking), it is necessary to parse the supplied HTML to validate that it does not use any dangerous syntax; this is a non-trivial task.
