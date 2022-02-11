# Flag 00

- Access to Snow-Crash VM using level00/level00 credential
```
ssh -p 4242 level00@10.11.100.146
```

- `ll`
> nothing interesting

- Check /etc/passwd
```
level00:x:2000:2000::/home/user/level00:/bin/bash
flag00:x:3000:3000::/home/flag/flag00:/bin/bash
```

- Find in / all files that the user level00 is the owner
```
find / -user level00 2> /dev/null
```
> nothing interesting

- Find in / all files that the user flag00 is the owner
```
find / -user flag00 2> /dev/null
```
```
/usr/sbin/john
/rofs/usr/sbin/john
```

- Cat the both files
```
cdiiddwpgswtgt
```

- Try to access to flag00
```
su flag00
Password: 
```

```
su: Authentication failure
```

- Decrypt the string with Caesar Cipher
> So it's a rote 15 => nottoohardhere

- Try to access to flag00 user and get the flag
```
level00@SnowCrash:~$ su flag00
Password: 
```

```
Don't forget to launch getflag !
```

```
getflag
```

```
Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
```

