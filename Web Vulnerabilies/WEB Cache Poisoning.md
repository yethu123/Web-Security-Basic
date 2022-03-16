
 - Using Burp Suite Param miner

 Header for Proxy

```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For
```
Vulnerable Lab by James Kettle

```
https://hackxor.net/mission?id=8
```
 Route Poisoning
```
GET /? HTTP/1.1
Host: transparency.hackxor.net
X-Forwarded-Host: https://analytics.hackxor.net/
```
REF
https://portswigger.net/blog/practical-web-cache-poisoning
