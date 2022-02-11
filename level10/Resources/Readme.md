# Flag 10

- `ll`
```
-rwsr-sr-x+ 1 flag10  level10 10817 Mar  5  2016 level10*
-rw-------  1 flag10  flag10     26 Mar  5  2016 token
```

- `./level10`
``` 
./level10 file host
        sends file to host if you have access to it
```

- I think that this binary send files to remote host, let's do some tests
```
~$ ./level10
./level10 file host
        sends file to host if you have access to it

~$ ./level10 token 
./level10 file host
        sends file to host if you have access to it

~$ ./level10 token localhost
You don't have access to token

~$ touch test
touch: cannot touch `test': Permission denied

~$ touch /tmp/test

~$ ./level10 /tmp/test localhost
Connecting to localhost:6969 .. Unable to connect to host localhost

~$ ./level10 /tmp/test 10.11.9.7
Connecting to 10.11.9.7:6969 .. Unable to connect to host 10.11.9.7

~$ ./level10 /tmp/test 10.11.9.7:6969
Connecting to 10.11.9.7:6969:6969 .. Unable to connect to host 10.11.9.7:6969

~$ netstat -lntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:4242            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5151          0.0.0.0:*               LISTEN     
tcp6       0      0 :::4646                 :::*                    LISTEN     
tcp6       0      0 :::4747                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::4242                 :::*                    LISTEN     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          

~$ ./level10 /tmp/test localhost:5151
Connecting to localhost:5151:6969 .. Unable to connect to host localhost:5151

~$ ufw allow 6969
ERROR: You need to be root to run this script
```

- So its a binary use 6969 port to send a file to remote host, I'm trying to open the port but don't have permissions






