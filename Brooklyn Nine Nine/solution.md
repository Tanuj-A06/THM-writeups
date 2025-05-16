Boot up the machine and run some recon.

Nmap:
![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20184316.png)

This tells us that FTP,SSH and a web-app is up and running.

## Method 1:

FTP:
![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20184654.png)

There is a txt file present, copy that to your local machine vai 'get'
``get <name_of_file>.<extension>``

Reading the contents:
![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20184857.png)

We know that the user 'jake' has a very weak password.

We can exploit this, by running a brute force on the ssh service vai hydra.

![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20185157.png)

#### User flag

We have cracked the password. Loggin in as jake with the cracked password.

![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20185432.png)

We find the user flag in another directory of the user 'holt'.

#### Privilege Escalation:

![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20185642.png)

We can use 'less' without any hindrence. Let's try to escalate priveleges to root.

We have a privilege escalation command.
```
sudo less /etc/profile
!/bin/sh
```

![image](/Brooklyn%20Nine%20Nine/img/Method1/Screenshot%202025-05-16%20190044.png)

With just that we are root, and we are also done with the room.


## Method 2:

Web-Page:

Visiting the web-page:
![image](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20191109.png)

Viewing the source-code:

This is intresting
![image](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20191232.png)

Getting the image down to the local machine

Command:``get 'http://<machine-ip>/brooklyn99.jpg'``

Using stegcracker to find the hidden meta-data.

![iamge](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20192010.png)

We get the meta-data. Looking at the contents.

#### User flag.

![image](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20192134.png)

We get password for a account. Logging in with ssh.

Logging in and getting the user flag.

![image](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20192305.png)

#### Privilege Escalation

![image](/Brooklyn%20Nine%20Nine/img/Method2/Screenshot%202025-05-16%20192606.png)

We have a privilege escalation command.
```
sudo nano
^R^X
reset; sh 1>&0 2>&0
```

And boom we are root, and the room is solved.