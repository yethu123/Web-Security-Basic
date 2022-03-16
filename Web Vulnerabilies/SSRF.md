## Server Side Request Forgery

**Reference**

```
https://www.owasp.org/index.php/Server_Side_Request_Forgery
https://blog.orange.tw/2017/07/how-i-chained-4-vulnerabilities-on.html
```
 - Must have server and client
 
 `$Sever_ddress/ssrf.php?url=http://localhost/intranet(fromServer).php`
 
  `<?php
    echo $_GET['name']
    ?> `  
