# Lemon-Duck Malware Analysis 
Lemon-Duck Malware is a monerocrypto-mining malware that convert the server resource into crytocurrency mining after infection.
Lemon Duck was written in Python language and use fileless infection way by using Powershell modules. The attacker use SMB vulnerability (CVE-2017-0144) explotation and brute-force attack through the network.

1.Malware Execution
Using Windows Virtual Machine and Powershell to execute the given malware payload then analyze it using Event Viewer program.

2.Event Viewer
In the event viewer log, navigate to

Application and Services Logs>Microsoft>Windows>Powershell>Operational

After digging the log, i found a full plain code that use to execute the malware payload as the image given.

3.Analyzing the code
First the malware execute a command to uninstall antivirus software like Eset, Kaspersky, Avast,Norton Security and Malwarebyte by launching wmic.exe on cmd program. It also scan program that use avp, security and antivirus name. The malware schedule a task name blackball by store persistence mechanism payload and connect to the command and control domain in the code.This malware also use netsh.exe program to open port 65529 and connect to the port.Then it will add firewall rule name deny445 and deny135 that will block any connection with port 445 and 135. At the end of the code, this malware try to delete 3 schedule task name Rtsa2, Rtsa1 and Rtsa.
