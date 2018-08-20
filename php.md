---
title: PHP
created_at: 2017-10-19 14:32:00 +0400
kind: cheatsheet
keywords: [code, cheatsheet]
---

# PHP

## Dealing with browsers caching files

https://php.net/manual/en/function.filemtime.php#81194

```php
<?php 
echo '<link rel="stylesheet" type="text/css" href="style.css?' . filemtime('style.css') . '" />'; 
?> 
```

## Quick and dirty code cache

https://php.net/manual/en/function.filemtime.php#98284

```php
<?php
$cache_file = 'URI to cache file';
$cache_life = '120'; //caching time, in seconds

$filemtime = @filemtime($cache_file);  // returns FALSE if file does not exist
if (!$filemtime or (time() - $filemtime >= $cache_life)){
    ob_start();
    resource_consuming_function();
    file_put_contents($cache_file,ob_get_flush());
}else{
    readfile($cache_file);
}
?>
```
