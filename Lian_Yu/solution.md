Boot up the machine and enumarate the given IP with nmap.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20205612.png)

FTP, SSH and a web-app is up.

Visiting the FTP service with 'anonymous'

![image](/Lian_Yu/img/Screenshot%202025-05-23%20205842.png)

Intresting this didn't work. Visiting the web-app.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20210051.png)

Nothing intresting on the web-page, and neither anything in the source code.

Let's try to enumerate further with 'gobuster', we will the scan to complete before exploring furter.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20211631.png)

We find an endpoint 'island'.
Visiting it we find something intresting.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20211744.png)

Probably a password, let's note that down and move forward.

Enumerating the endpoint found.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20211920.png)

And visiting it we find nothing intresting but the source code gives us an hint.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20212025.png)

Again using gobuster but now only searching for a endpoint with '.ticket' as an extension.

Syntax:
``
gobuster dir -u <site.name> -w <wordlist> -x <.extension>
``

![image](/Lian_Yu/img/Screenshot%202025-05-23%20213021.png)

Bingo, we got something.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20213314.png)

It's probably an encrypted password, it was base58 cipher dcoding it we get a password.

Loggin in to 'FTP' with the name we found before and the password we now found.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20213558.png)

We are in, now looking around.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20213827.png)

Copying everything in our remote desktop.

Nothing intresting in the images, other than a few rabbit holes, trying to extract hidden text from '.jpg' file with stegcracker.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20215413.png)

Nicee, viewing the file type of the extracted file.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20215558.png)

Intresting, converting it into a zip archive extension and unzipping to get the cotents.

The .other_user has the ssh username and the password was in the zip file.

Loggin in with ssh.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20220018.png)

Yep we are in, now escalating to root.

![image](/Lian_Yu/img/Screenshot%202025-05-23%20220123.png)

Escalating our privileges with that binary,

Command:

``
sudo pkexec /bin/sh
``

![image](/Lian_Yu/img/Screenshot%202025-05-23%20220334.png)

And the room has been rooted.