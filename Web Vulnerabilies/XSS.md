 1. Stored XSS (Persistent XSS)  
 2. Reflected XSS (Non-persistent XSS) 
 3. DOM-based XSS

REF 

    https://portswigger.net/web-security/cross-site-scripting
    https://brutelogic.com.br/blog/dom-based-xss-the-3-sinks/
    https://blog.qualys.com/product-tech/2017/03/06/smart-dom-xss-detection-in-qualys-was

 **What’s the impact of XSS?**
An attacker who exploits a cross-site scripting vulnerability is typically able to:
-   Impersonate or masquerade as the victim user
-   Hijack a user’s session
-   Perform unauthorized activities
-   Steal sensitive information
-   Perform phishing attacks
-   Capture the user’s login credentials.
-   Capture keystrokes
-   Deface the website.
-   Inject trojan functionality into the website.

[cheatsheethtml5](https://html5sec.org/)

LAB - [Appspot](https://google-gruyere.appspot.com/)

### DOM XSS
The script code never reaches the server if we use the **#** character.
It is seen as a fragment and the browser does not forward it. 

 **Sources and Sinks**

**Sources**: The source is the injection point for the malicious JavaScript. With DOM XSS, the sources are on the client. Payloads including malicious JavaScript code injected into sources with or without some processing could then reflect in the DOM or execute.

Examples of DOM XSS sources are document.URL, cookies, referer header.

**Sinks**: The sink is the reflection point that eventually executes (or helps with execution of) the malicious JavaScript injected through the source. These are usually locations on the DOM or Browser Object that can change and invoke code, or they are JavaScript routines that allow direct JavaScript execution.

Examples of easy-to-exploit sinks are eval, document.write, setTimeout.


LAB - [Public Firing](https://public-firing-range.appspot.com/)
IDE attack detection tools will fail to detect this attack.

 My Note
 1. Cookies can be stolen.
 2. Java script execution 
 3. Advanced handler like
 4. Obfuscation
 5. Bypass or Escape
 6. Avoiding
 7. HtmlSpecialCharacter works encoding
 8. After hash sign, the browser encode it.
 10. can execute script when you sent to other users. 
Some Useful Payload
-  `<img src=x onerror=alert(1)>`
- `<script> prompt(1)</script>`
- `<svg onload=alert(1) `
- `<a onclick=alert(1)>`
- `<body onload=alert(1)> `
