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
![image](https://github.com/user-attachments/assets/dcfcb67a-bee2-470b-8fed-43b75701ca3d)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

systemctl start postgresql
>systemctl start postgresql
>msfdb init


Invoke msfconsole:



## OUTPUT:

![image](https://github.com/user-attachments/assets/8ff19b23-1c5f-4554-b84b-7d5787b0102e)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/ae352bd2-0b07-47cb-81ba-9dcb45191639)

Port Scanning: 

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). 
msf > nmap -sT 192.168.1810/24 -p1-1000


OUTPUT:

![image](https://github.com/user-attachments/assets/50678d4b-30ad-4ebe-a650-4a40a0b4ae65)
step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. 
msf > db_nmap 192.168.181.0/24

OUTPUT:
![image](https://github.com/user-attachments/assets/9496b1ec-71c3-4d2c-b60c-c351b427a6a2)
multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary 
kali > ls -l

OUTPUT:

![image](https://github.com/user-attachments/assets/209fc967-05bc-4384-b0d6-ab0bbb5f73d4)
Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

OUTPUT:
![image](https://github.com/user-attachments/assets/5326ac65-fd57-482c-99f4-3dee54cd4cc5)
The info command provides information regarding a module or platform,
![image](https://github.com/user-attachments/assets/e55e25d9-00f8-4635-858f-f76b9c65f3bb)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init
MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/user-attachments/assets/356bf63d-07f4-406f-9db8-38fae67eb26a)
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. 
search type:auxiliary mysql
![image](https://github.com/user-attachments/assets/8b7a3db7-5892-4b28-9603-ac5bbd6c3a88)
use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/user-attachments/assets/383c6524-da6b-4939-8e81-f5c9f002ab2d)
Use the set rhosts command to set the parameter and run the module, as follows:

![image](https://github.com/user-attachments/assets/0ca95856-9e64-44b0-8c3f-1c9a48e84d6f)
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/user-attachments/assets/48d14232-9a72-4457-b72e-d1bd6e025ccd)
set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

>set BLANK_PASSWORDS true
![image](https://github.com/user-attachments/assets/500b4062-cdfd-4726-848f-be0b0c1757c8)




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
