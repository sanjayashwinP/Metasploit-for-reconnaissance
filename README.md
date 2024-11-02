# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
### NAME:SANJAY ASHWIN P
### REG NO:212223040181
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


## OUTPUT:
![WhatsApp Image 2024-11-02 at 12 30 07_8df0b53e](https://github.com/user-attachments/assets/79d43e11-fb91-46b4-9797-e871814240ef)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

systemctl start postgresql
>systemctl start postgresql
>msfdb init


Invoke msfconsole:



## OUTPUT:

![WhatsApp Image 2024-11-02 at 12 31 07_e545e9ca](https://github.com/user-attachments/assets/b62a3267-f4d6-4e4b-9431-08861e5b9186)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/9b74f2a5-8275-4e53-944d-2dcfe0f4d196)


Port Scanning: 

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). 
msf > nmap -sT 10.0.2.15/24 -p1-900


OUTPUT:

![WhatsApp Image 2024-11-02 at 12 40 06_ae67a174](https://github.com/user-attachments/assets/104a3f4f-723b-4db9-a9d7-aa02532d7c74)

step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. 
msf > db_nmap 10.0.2.15

OUTPUT:
![WhatsApp Image 2024-11-02 at 12 55 25_d19ab84d](https://github.com/user-attachments/assets/192f38bb-9718-4b8d-87e7-6ee9323e4ef2)

multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary 
kali > ls -l

OUTPUT:

![WhatsApp Image 2024-11-02 at 13 01 38_e9da5168](https://github.com/user-attachments/assets/fa55feb7-05ac-4717-aab3-646df48433e5)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

OUTPUT:
![WhatsApp Image 2024-11-02 at 13 05 14_cb6f602f](https://github.com/user-attachments/assets/510cce24-ce6f-4b9b-9eb7-a396a9c33074)

The info command provides information regarding a module or platform,
![WhatsApp Image 2024-11-02 at 12 31 41_11f68374](https://github.com/user-attachments/assets/bf3311c2-71a4-42f9-a277-08dcfd99bc23)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init
MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![WhatsApp Image 2024-11-02 at 13 09 36_874020c7](https://github.com/user-attachments/assets/a0979820-750d-4457-9294-40dc25b67de9)   


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. 
search type:auxiliary mysql

![WhatsApp Image 2024-11-02 at 13 11 10_0d07d0bf](https://github.com/user-attachments/assets/3e9ecca3-52f9-4728-839f-1a7e8dae226c)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

![WhatsApp Image 2024-11-02 at 13 13 08_7ba5739d](https://github.com/user-attachments/assets/0bb280ae-2a91-457f-99a3-43853c2d9209)


Use the set rhosts command to set the parameter and run the module, as follows:

![WhatsApp Image 2024-11-02 at 13 15 03_77d84127](https://github.com/user-attachments/assets/3e9fa4bb-1f00-4253-8073-cdfb6e3d7d38)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![WhatsApp Image 2024-11-02 at 13 18 29_9ca3b04d](https://github.com/user-attachments/assets/7f354e7c-029f-4ed4-837c-4b54790de14d)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

>set BLANK_PASSWORDS true

![WhatsApp Image 2024-11-02 at 13 35 24_53b1c121](https://github.com/user-attachments/assets/ed1dfaec-640c-40c9-a6f8-1dad1db6e0cd)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
