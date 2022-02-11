# Flag 02

- Access to Snow-Crash VM level02/f2av5il02puano7naaf6adaaf credential
```
e1r9p7% ssh -p 4242 level02@10.11.100.146
```

- `ll`
```
----r--r-- 1 flag02  level02 8302 Aug 30  2015 level02.pcap
```

- Search in google how to read the data of a pcap file with wireshark tool
https://osqa-ask.wireshark.org/questions/15374/dump-raw-packet-data-field-only/

- Copy pcap file from local to Kali
```
level02@SnowCrash:~$ scp level02.pcap kali@10.11.100.41:/home/kali/.
```

- Change permissions to read it 
```
chmod +r level02.pcap 
```

- Print just the data, in ASCII format.
```
tshark -r level02.pcap -T fields -e data
```

```
fffd25

fffc25

fffb26fffd18fffd20fffd23fffd27fffd24
fffe26fffb18fffb20fffb23fffb27fffc24
fffa2001fff0fffa2301fff0fffa2701fff0fffa1801fff0
fffa200033383430302c3338343030fff0fffa2300536f646143616e3a30fff0fffa270000444953504c415901536f646143616e3a30fff0fffa1800787465726dfff0
fffb03fffd01fffd22fffd1ffffb05fffd21
fffd03fffc01fffb22fffa220301000003620304020f05000007621c08020409421a0a027f0b02150f02111002131102ffff1202fffffff0fffb1ffffa1f00b10031fff0fffd05fffb21
fffa220103fff0
fffa220107fff0
fffa2103fff0fffb01fffd00fffe22
fffd01fffb00fffc22
fffa220303e20304820f07e21c08820409c21a0a827f0b82150f82111082131182ffff1282fffffff0

0d0a4c696e757820322e362e33382d382d67656e657269632d70616520283a3a666666663a31302e312e312e322920287074732f3130290d0a0a010077777762756773206c6f67696e3a20

6c
006c

65
0065

76
0076

65
0065

6c
006c

58
0058

0d
01

000d0a50617373776f72643a20

66

74

5f

77

61

6e

64

72

7f

7f

7f

4e

44

52

65

6c

7f

4c

30

4c

0d

000d0a

01

000d0a4c6f67696e20696e636f72726563740d0a77777762756773206c6f67696e3a20
```

- Decode it with https://www.convertstring.com/EncodeDecode/HexDecode
```
ÿý%ÿü%ÿû&ÿýÿý ÿý#ÿý'ÿý$ÿþ&ÿûÿû ÿû#ÿû'ÿü$ÿú ÿðÿú#ÿðÿú'ÿðÿúÿðÿú �38400,38400ÿðÿú#�SodaCan:0ÿðÿú'��DISPLAYSodaCan:0ÿðÿú�xtermÿðÿûÿýÿý"ÿýÿûÿý!ÿýÿüÿû"ÿú"��b��b	B
ÿÿÿÿÿðÿûÿú�±�1ÿðÿýÿû!ÿú"ÿðÿú"ÿðÿú!ÿðÿûÿý�ÿþ"ÿýÿû�ÿü"ÿú"ââ	Â
ÿÿÿÿÿð
Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

�wwwbugs login: l�le�ev�ve�el�lX�X
�
Password: ft_wandrNDRelL0L
�
�
Login incorrect
```

- Try to access to flag01 to get the flag using `ft_wandrNDRelL0L`
```
level02@SnowCrash:~$ su flag02
Password: 
Don't forget to launch getflag !
flag02@SnowCrash:~$ getflag
Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```









