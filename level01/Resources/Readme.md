# Flag 01

- Access to Snow-Crash VM level01/x24ti5gi3x0ol2eh4esiuxias credential
```
ssh -p 4242 level01@10.11.100.146
```

- `ll`
> nothing interesting

- Check /etc/passwd
```
flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
```

- After many attempts to find a good tool to crack this password, I found john tool, so I installed Kali linux to use it.


- Copy /etc/passwd file from VM Kali 

- Update and install john tool in Kali
```
apt update && apt install john -y
```

- Run john tool to crack pwd
```
john passwd
```

```
abcdefg          (flag01)
```

- Try to access to flag01 to get the flag
```
level01@SnowCrash:~$ su flag01
Password: 
Don't forget to launch getflag !
flag01@SnowCrash:~$ getflag
Check flag.Here is your token : f2av5il02puano7naaf6adaaf
```