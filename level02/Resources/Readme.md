# Flag 02

- `ll`
+ we find 
`----r--r-- 1 flag02  level02 8302 Aug 30  2015 level02.pcap`

- So I will try to readit with wireshark in Kali
- conf ssh in kali
- use scp to copy pcap file to kali
`scp level02.pcap kali@10.11.100.41:/home/kali/.`

- Change permissions to read it and open it with wireshark
- search in google "tshark data field"
- Use wireshark cli
https://osqa-ask.wireshark.org/questions/15374/dump-raw-packet-data-field-only/
`tshark -r infile -T fields -e data`
- decode it with https://www.convertstring.com/EncodeDecode/HexDecode
- found "Password: ft_wandrNDRelL0L"
- try to swuitch to user flag02
and done: 
- Check flag.Here is your token : kooda2puivaav1idi4f57q8iq


## Abstract
- Password flag02: ft_wandrNDRelL0L
- Password level03: kooda2puivaav1idi4f57q8iq









