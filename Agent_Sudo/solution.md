Boot up the machine and then enumerate to find the services running.

nmap

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20102602.png)

Visiting the service on port 80

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20103107.png)

Intresting, fireup Burp and manipulate the requests.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20103414.png)

'R' gives us an intresting responce, now going from A to Z we get a hit on 'C'.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20103652.png)

Visiting this endpoint, we get something intresting.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20103755.png)

Since the password of agent-C is weak, we can use hydra to brutefore for its password. Let's try with bruteforcing FTP first.

Using rockyou.txt we get a hit.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20104202.png)

Logging in FTP and copying everything to our remote desktop.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20104417.png)

```
└─$ cat To_agentJ.txt 
Dear agent J,

All these alien like photos are fake! Agent R stored the real picture inside your directory. Your login password is somehow stored in the fake picture. It shouldn't be a problem for you.

From,
Agent C
```

Ok we use steghide on .jpg and zsteg on .png to find out any hidden info, since the .jpg image is most probably password protected i used stegseek which will try for default passwords.

```
└─$ stegseek cute-alien.jpg /usr/share/wordlists/rockyou.txt 
StegSeek 0.6 - https://github.com/RickdeJager/StegSeek

[i] Found passphrase: "Area51"           
[i] Original filename: "message.txt".
[i] Extracting to "cute-alien.jpg.out".
```

Nice, and the png contains the zip file which inturn contains the password for this image, but now thats not required.(To extract that zip from image use binwalk. 
Syntax: ``binwalk e <image>.png``)

```
└─$ cat cute-alien.jpg.out 
Hi <Redacted>,

Glad you find this message. Your login password is <Redacted>

Don't ask me why the password look cheesy, ask agent R who set this password for you.

Your buddy,
Agent-C
```

This has a leaked credential in it. Using it on ssh, we get the user-flag.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20105555.png)

Let's lookup for '/bin/bash' exploit on the internet.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20105746.png)

We do find a CVE, lest try the exploit.

![image](/Agent_Sudo/img/Screenshot%202025-06-10%20105846.png)

Boom, we are root!!

Now get the root flag and complete the aditional questions along the way.