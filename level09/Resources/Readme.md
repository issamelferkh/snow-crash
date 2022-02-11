# Flag 09

- Access to Snow-Crash VM using level09/25749xKZ8L7DkSCwJkT9dyv6f credentials
```
e1r9p7% ssh -p 4242 level09@10.11.100.146
```

- `ll`
```
-rwsr-sr-x 1 flag09  level09 7640 Mar  5  2016 level09*
----r--r-- 1 flag09  level09   26 Mar  5  2016 token
```

- Try to run level09
```
level09@SnowCrash:~$ ./level09 
You need to provied only one arg.
```

- More Attempts
```
level09@SnowCrash:~$ ./level09 token 
tpmhr

level09@SnowCrash:~$ ./level09 aaaaa
abcde

level09@SnowCrash:~$ ./level09 AAAAA
ABCDE

level09@SnowCrash:~$ ./level09 11111
12345
```

- So, I understand that the program decrypt the 1st arg by adding for each char in the arg his index to his ascii

> Example, decrypt 1st test: 
t-0 -> t
p-1 -> o
m-2 -> k
h-3 -> e
r-4 -> n
So result is: token

- Write a simple C prog to decrypt it

``` c
#include <unistd.h>

int main(int ac, char** av) {
	char* s = av[1];

	int i = 0;
	while (s[i] != 0) {
		char tmp = s[i] - i;
		write(1, &tmp, 1);
		i++;
	}
	write(1, "\n", 1);
	return 0;
}
```

- Download the token from Snow Crach VM
```
scp -P 4242 level09@10.11.100.146:/home/user/level09/token .
```

- Decrypt the cat token
```
./script $(cat token )
f3iji1ju5yuevaus41q1afiuq

level09@SnowCrash:~$ su flag09
Password: 
Don't forget to launch getflag !

flag09@SnowCrash:~$ getflag
Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
```