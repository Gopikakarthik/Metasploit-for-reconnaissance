# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

## Step 2:
Investigate on the various categories of tools as follows:

## Step 3:
Open terminal and try execute some kali linux commands

## Step4: 
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## PROGRAM:
Find out the ip address of the attackers system

## OUTPUT:
![326267106-f1e503de-3180-4bcf-b7ee-465d18284833](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/c14085bc-0fd3-449d-b109-36d5bd008d9a)



## Invoke msfconsole:
## OUTPUT:
![326267123-a5910b23-34ee-4de3-9024-7c449304f4b7](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/020d33f2-bb47-4094-ac41-14b4cbd37bc3)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![326267157-4c8c5284-f372-4efb-bc7e-f3ced81b159c](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/4ad72036-a0fd-49da-a8da-062090b0fd7e)


Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![326267219-cadb47ce-e16a-4414-aa12-806bfb675db6](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/57509ff5-d550-48d8-bb54-3c00f9a64ea1)



## OUTPUT:
![326267233-24c11b6c-3806-47ce-9451-e18365478d75](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/395c0705-fb35-4dd5-8d49-d5b856d036fc)



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![326267261-adf159ba-90c8-465f-a4a5-17bbeed7a20d](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/cc0431d7-197d-4822-9bd2-4c722e8f4655)

![326267270-81893844-cac8-4197-9ad7-66324c0a0285](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/dda08e7f-95a5-4345-a81f-742ff55f4ad0)



Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

![326267304-b2c2e737-483a-42ae-9189-d2f5984cb960](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/43a52cbe-3ecf-41ab-9e33-2e09e7f1698e)


The info command provides information regarding a module or platform

## OUTPUT:
![326267340-50fef82f-24cc-488a-800d-eadea2e57128](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/3ba36402-44f9-42fa-96c2-882777c9f70a)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init ##MYSQL ENUMERATION Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address> 

![326267390-7ae76a37-ab78-46d4-8585-ac2a65b1f372](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/03ddb4b1-87f6-43e2-82c5-12e7542ca439)



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![326267356-7c6625e9-5855-49a5-bcce-2a941b8000cf](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/3d47ff33-70d7-440b-b7c6-c8b5cff86ed4)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version


![326267416-1df789c6-1c31-4d52-8962-fca3b3d25907](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/11aa3dca-86b9-41ac-bcb2-7417facaf0a4)



Use the set rhosts command to set the parameter and run the module, as follows:

![326267448-be445d81-bae0-40a4-b770-1adf09ee1f8b](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/af92c23b-c9a5-4bc7-a40d-b6402a2fe836)



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![326438859-9a190717-5e24-45d6-ab92-e091e93fef1e](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/862f535c-4a19-4b63-a9df-44c32a4dcc40)




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true


![326439020-3ebbdc76-ec11-4793-98e8-d59b0e826e77](https://github.com/Gopikakarthik/Metasploit-for-reconnaissance/assets/121235427/362b03a1-1dcd-4923-a514-4b084dca40eb)


## RESULT:
The Metasploit framework for reconnaissance is examined successfully## EXECUTION STEPS AND ITS OUTPUT:
