# SQL Injection in AudimexEE ver X.X.X.X

### Overview
AudimexEE before X.X.X is vulnerable to SQL Injection. An attacker with limited privileges (Auditor) can achieve a SQL injection that can lead in data leakage.

### Description
The vulnerability, present in the XXXXXXXXX, can be exploited via 'XXXXX' parameters, using a payload for trigger a error-based or boolean-based blind sql injection.

### Impact
This vulnerability allows attackers with limited privileges to execute SQL queries on the server.

### Timeline
- 2020-10-09: Discovered and reported to Audimex
- 2020-10-09: Got instant response from Audimex development team, "Thanks for your analysis report. We will evaluate your finding and get back to you soon with our feedback."
- 2020-10-12: Audimex fixed this issue in audimexEE version X.X.X.X
- 2020-10-23: First public PoC

### Suggestions

The most effective way to prevent SQL injection attacks is to use parameterized queries (also known as prepared statements) for all database access. This method uses two steps to incorporate potentially tainted data into SQL queries: first, the application specifies the structure of the query, leaving placeholders for each item of user input; second, the application specifies the contents of each placeholder. Because the structure of the query has already been defined in the first step, it is not possible for malformed data in the second step to interfere with the query structure. You should review the documentation for your database and application platform to determine the appropriate APIs which you can use to perform parameterized queries. It is strongly recommended that you parameterize every variable data item that is incorporated into database queries, even if it is not obviously tainted, to prevent oversights occurring and avoid vulnerabilities being introduced by changes elsewhere within the code base of the application.

You should be aware that some commonly employed and recommended mitigations for SQL injection vulnerabilities are not always effective:

- One common defense is to double up any single quotation marks appearing within user input before incorporating that input into a SQL query. This defense is designed to prevent malformed data from terminating the string into which it is inserted. However, if the data being incorporated into queries is numeric, then the defense may fail, because numeric data may not be encapsulated within quotes, in which case only a space is required to break out of the data context and interfere with the query. Further, in second-order SQL injection attacks, data that has been safely escaped when initially inserted into the database is subsequently read from the database and then passed back to it again. Quotation marks that have been doubled up initially will return to their original form when the data is reused, allowing the defense to be bypassed.

- Another often cited defense is to use stored procedures for database access. While stored procedures can provide security benefits, they are not guaranteed to prevent SQL injection attacks. The same kinds of vulnerabilities that arise within standard dynamic SQL queries can arise if any SQL is dynamically constructed within stored procedures. Further, even if the procedure is sound, SQL injection can arise if the procedure is invoked in an unsafe manner using user-controllable data.

### Proof of concept (POC)
#### Reproducing Steps

![Screenshot](index.jpg)

### Discovered by
#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) from [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)
