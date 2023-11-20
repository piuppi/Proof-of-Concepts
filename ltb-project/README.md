# Vulnerability found in LTB (a.k.a. LDAP Tool Box) Self Service Password 

### Overview
LTB Self Service Password is an open-source PHP application that allows users to change their password in an LDAP directory. The application can be used on standard LDAPv3 directories (OpenLDAP, OpenDS, ApacheDS, Sun Oracle DSEE, Novell, etc.) and also on Active Directory.<br><br>Features include: Standard password change, Reset by questions, Token sent by e-mail and Token sent by SMS.


### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
 
### Vulnerability Details

#### {RESERVED CVE} :
LTB (a.k.a. LDAP Tool Box) Self Service Password before version 1.5.4 allows an unauthenticated attacker to hijack the SMS verification code to an arbitrary phone number, which leads to changing the user's password without any notification.

