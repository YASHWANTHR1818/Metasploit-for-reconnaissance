# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="928" height="376" alt="Screenshot 2026-08-20 105028" src="https://github.com/user-attachments/assets/6a5fa921-0aa5-4261-9252-830185c34717" />

Invoke msfconsole:
## OUTPUT:

<img width="647" height="408" alt="Screenshot 2026-08-25 194426" src="https://github.com/user-attachments/assets/d9448447-99ba-4a11-ab0e-8642ed5a99c3" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1579" height="997" alt="Screenshot 2026-08-20 110402" src="https://github.com/user-attachments/assets/c4375ff1-9625-4948-9fb6-2b5e810ffeef" />

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="1617" height="532" alt="Screenshot 2026-09-01 135444" src="https://github.com/user-attachments/assets/b55b1475-e7a4-4e1d-828f-1421d041157b" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="1605" height="370" alt="Screenshot 2026-09-01 135916" src="https://github.com/user-attachments/assets/0b229889-8c9c-48c0-bdf1-9e0db9bc9b9b" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="722" height="463" alt="Screenshot 2026-08-20 113042" src="https://github.com/user-attachments/assets/ddd5cc6d-28ed-49db-8261-9be0f17cda9d" />

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="986" height="973" alt="image" src="https://github.com/user-attachments/assets/a9b94c36-9974-4bff-82d9-44e67c0a824e" />

The info command provides information regarding a module or platform,

<img width="1095" height="754" alt="Screenshot 2026-08-20 114332" src="https://github.com/user-attachments/assets/35a70eee-d566-4626-80f2-d7378cb165b9" />

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="1598" height="326" alt="Screenshot 2026-09-01 135015" src="https://github.com/user-attachments/assets/84a532a3-6e53-4cfc-954d-1c01eca3f672" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1045" height="541" alt="Screenshot 2026-08-21 103525" src="https://github.com/user-attachments/assets/38ed7e91-35f9-4056-ae13-04417f9dd13a" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="934" height="372" alt="Screenshot 2026-08-21 104519" src="https://github.com/user-attachments/assets/1cc7ae67-85dd-4a4c-9c8a-0dec0a9f22f9" />

Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="665" height="133" alt="Screenshot 2026-08-21 104717" src="https://github.com/user-attachments/assets/408f0ad0-5606-4da9-8aa3-f6c7f4158a14" />

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="923" height="607" alt="Screenshot 2026-08-21 104859" src="https://github.com/user-attachments/assets/e23af83a-45b9-45c8-95c1-c9431c343b6a" />

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="802" height="222" alt="Screenshot 2026-08-21 104210" src="https://github.com/user-attachments/assets/5597ad2b-e19a-43c2-bb36-c5ea5aca530b" />

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
