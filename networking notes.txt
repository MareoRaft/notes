TCP - control
port numbers!

21 ftp
22 ssh
23 telnet
25 smtp - simple mail
80 - http - hypertext
443 - https
110 - pop - post office
143 - imap

7 layers of networking!
http://www.lensenet.com/OSI_Model/OSI_7-Layer_Model.html

COMMANDS:
ping IP IP IP ... (no IP hopping on mac)
-a - alert on each ping
-i # - interval
-c # - count - # of pings
-f - flood (no mac)
-V - version (no mac)
-s - size of packet (it will add 8 bytes ('header' checksum?))
-w - time deadline
-R - show route of how ECHO_REQUEST sent and ECHO_REPLY received
---------
localhost resolves to 127.0.0.1
0 resolves to 127.0.0.1 (no mac)
url resolves to IP
