# Vulnerabilities discovered in Microsoft Office365 Outlook Web Access (https://outlook.office.com/owa)

### Overview
Outlook Web Access is a personal information manager web app from Microsoft. It is included in Microsoft 365, Office 365, Exchange Server 2016/2019, and Exchange Online. It includes a web-based email client, a calendar tool, a contact manager, and a task manager.

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
 
### Description

#### A Stored cross-site scripting (XSS) vulnerability in Microsoft Office365 OWA, which allows remote attackers to inject arbitrary HTML or web scripts by creating an ad-hoc email signature containing a malicious link, which can lead to data leakage. The XSS is triggered whenever a new email message is created, however, running a logoff and logon no longer triggers it.

Stored cross-site scripting vulnerabilities arise when user input is stored and later embedded into the application's responses in an unsafe way. An attacker can use the vulnerability to inject malicious JavaScript code into the application, which will execute within the browser of any user who views the relevant application content. The attacker-supplied code can perform a wide variety of actions, such as stealing victims' session tokens or login credentials, performing arbitrary actions on their behalf, and logging their keystrokes. Methods for introducing malicious content include any function where request parameters or headers are processed and stored by the application, and any out-of-band channel whereby data can be introduced into the application's processing space (for example, email messages sent over SMTP that are ultimately rendered within a web mail application). Stored cross-site scripting flaws are typically more serious than reflected vulnerabilities because they do not require a separate delivery mechanism in order to reach target users, and are not hindered by web browsers' XSS filters. Depending on the affected page, ordinary users may be exploited during normal use of the application. In some situations this can be used to create web application worms that spread exponentially and ultimately exploit all active users.

### Impact
An attacker, using phishing techniques, could have persuaded the victim to change the e-mail signature with the one attached by him, and then steal the user's cookies.

However the security impact of cross-site scripting vulnerabilities is dependent upon the nature of the vulnerable application, the kinds of data and functionality that it contains, and the other applications that belong to the same domain and organization. If the application is used only to display non-sensitive public content, with no authentication or access control functionality, then a cross-site scripting flaw may be considered low risk. However, if the same application resides on a domain that can access cookies for other more security-critical applications, then the vulnerability could be used to attack those other applications, and so may be considered high risk. Similarly, if the organization that owns the application is a likely target for phishing attacks, then the vulnerability could be leveraged to lend credibility to such attacks, by injecting Trojan functionality into the vulnerable application and exploiting users' trust in the organization in order to capture credentials for other applications that it owns. In many kinds of application, such as those providing online banking functionality, cross-site scripting should always be considered high risk.

### Proof of concept (POC)
#### Reproducing Steps

![](images/XSS-poc_R.gif)

##### Document cookie: 
![screenshoot](images/document-cookie_R.png)

##### Used payload:
```"></a></div><svg/onload=alert(String.fromCharCode(88,83,83))><!--```
    
```<%<!--'%><script>alert(document.cookie);</script -->```


### Suggestions
In most situations where user-controllable data is copied into application responses, cross-site scripting attacks can be prevented using two layers of defenses:
- Input should be validated as strictly as possible on arrival, given the kind of content that it is expected to contain. For example, personal names should consist of alphabetical and a small range of typographical characters, and be relatively short; a year of birth should consist of exactly four numerals; email addresses should match a well-defined regular expression. Input which fails the validation should be rejected, not sanitized.
- User input should be HTML-encoded at any point where it is copied into application responses. All HTML metacharacters, including < > " ' and =, should be replaced with the corresponding HTML entities (&lt; &gt; etc).
In cases where the application's functionality allows users to author content using a restricted subset of HTML tags and attributes (for example, blog comments which allow limited formatting and linking), it is necessary to parse the supplied HTML to validate that it does not use any dangerous syntax; this is a non-trivial task.

### Timeline
- **2019-06-25**: Discovered and reported to Microsoft
- **2019-06-25**: Got instant response from Microsoft Security Response Center, "Thank you for contacting the Microsoft Security Response Center (MSRC). Your report has been received and you should receive a follow-up message from the case manager once your case has been fully reviewed."
- **2019-06-26**: Got mail saying, "Thank you very much for your report.I have opened case '{redacted}' and the case manager, '{redacted}' will be in touch when there is more information."
- **2019-06-27**: Got mail saying, "Just a quick introduction, I'm the MSRC case manager who will be looking after this investigation moving forward. Thank you for reporting this to Microsoft responsibly - we appreciate your effort in doing so. At this moment the product team is investigating your report and I hope to have some feedback fairly soon."
- **2019-07-12**: Got mail saying, "We have successfully reproduced the issue that you reported to us.  We will be finishing our investigation and determining if we will address it in a security release."
- **2019-08-02**: Got mail saying, "We're happy to inform you that your case {redacted} is eligible for a $500 bounty award. Congratulations and thank you for your continued support in helping to secure some of the world's largest platforms, products, and services."
- **2019-09-09**: Got mail saying, "A fix has been confirmed for the issue you reported, We have resolved the issue you reported, and have closed this case."
