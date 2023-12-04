# Vulnerability found in LTB (a.k.a. LDAP Tool Box) Self Service Password 

### Overview
LTB Self Service Password is an open-source PHP application that allows users to change their password in an LDAP directory. The application can be used on standard LDAPv3 directories (OpenLDAP, OpenDS, ApacheDS, Sun Oracle DSEE, Novell, etc.) and also on Active Directory.<br><br>Features include: Standard password change, Reset by questions, Token sent by e-mail and Token sent by SMS.


### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
 
### Vulnerability Details

#### [CVE-2023-49032](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-49032) LTB (a.k.a. LDAP Tool Box) Self Service Password before version 1.5.4 allows an unauthenticated attacker to Hijack the SMS verification code to an arbitrary phone number, which leads to changing the user's password without any notification.

### Reference
https://github.com/ltb-project/self-service-password/issues/816

https://github.com/ltb-project/self-service-password/releases/tag/v1.5.4

### Timeline
- **2023-11-14**: Discovered and reported to LTP-PROJECT Devlopment Team
- **2023-11-14**: Got instant response from LTP-PROJECT Devlopment Team to address the issue
- **2023-11-20**: Got response from LTP-PROJECT Devlopment Team, "bug confirmed and patch provided privately..."
- **2023-11-22**: Version 1.5.4 containing the fix has been released by LTP-PROJECT Devlopment Team
- **2023-11-22**: I've requested a CVE ID from MITRE and am awaiting assignment


