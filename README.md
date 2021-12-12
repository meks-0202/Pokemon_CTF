# Pokemon_CTF
#### A begginer level CTF.

[Find the machine here](https://drive.google.com/file/d/1bZNuZXk_sBt9kNg0uuFez4Xti6Grf9tr/view?usp=sharing "Named link title")


## About The Machine

The vulnerable machine I made is a beginner friendly CTF-machine. A CTF stands for Capture the Flag, a game in which players put their skills to practice to solve problems or break into an opponent’s system. A machine with simple vulnerabilities involving Web Exploitation(Exploiting web page to find the flag) and Pwn(Exploiting a server to find the flag).

### My Virtual Lab Setup
* I used the latest Ubuntu version(Ubuntu 20.04 LTS) as victim machine.
* Kali linux 2021.1 as attacker machine.
### External Dependecies/Packages/Softwares
*  Apache2 (Apache web server) 2.4.41
*  PHP 7.4.3
### Hardware Requirments
* RAM: 512 MB
* HDD: 4 GB
* VRAM: 16+ MB

<img src="https://github.com/meks-0202/Pokemon_CTF/blob/7a0251d858a05cb1436b2a3b37ebea636b8790c2/assests/Page.png">

## Vulnerabilities Added
### > Anonymous Login
#### Severity : Low
Anonymous authentication is an FTP vulnerability that allows users to log in with a user name of FTP or anonymously. A user’s login credentials (username and password) and the commands used are unencrypted, visible, and vulnerable to access. At the same time, any data sent through FTP or is hosted on an anonymous FTP server is also left unprotected.

### > File Upload
#### Severity: Critical
File upload vulnerability allows us to upload any type of file (even the malicious files) to the server. Many websites allow file upload in one way or the other – some allow to upload jpg or png files as profile picture whereas some allow uploading other types of files like pdf, txt, mp3, mp4 etc. If the website does not validate the type of file being uploaded, it can lead to a complete server compromise.

### > Internal Portal Publicly accessible
#### Severity: Medium
The internal web portal is publicly accessible and may result in sensitive data exposure. These portals must be accessible only on the local network.

### > Privilege Escalation using Linux Capabilities (Binaries Capabilities)
#### Severtiy: Critical
Binaries can have capabilities that can be used while executing. For example, it's very common to find ping binary with cap_net_raw capability:
```bash
getcap /usr/bin/ping
/usr/bin/ping = cap_net_raw+ep
```
You can search binaries with capabilities using:
```bash
getcap -r / 2>/dev/null
```
If the binary has the Linux CAP_SETUID capability set or it is executed by another binary with the capability set, it can be used as a backdoor to maintain privileged access by manipulating its own process UID.
```bash
cp $(which perl) .
sudo setcap cap_setuid+ep perl

./perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh";'
```

## Steps to setup the machine
#### Step-1
Download the machine by clicking [_here_](https://drive.google.com/file/d/1bZNuZXk_sBt9kNg0uuFez4Xti6Grf9tr/view?usp=sharing).
#### Step-2 
Import the .ova file to your virtual box. Make sure the settings match the hardware requirments.
#### Step-3 
Keep network settings to NAT/bridged networks.
#### Step-4 
Get started with the machine, you'll find the IP to the machine on the login page that appears and <b>Voila!!</b>

## Happy Hacking! :)
