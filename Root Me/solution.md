Fire up nmap and gobuster to find the required things in the task 1 to 3.

For user and root flag use the following steps:

1) navigate to /panle endpoint here you can upload anything (Hopefully a shell)
2) .php extensions throw an error change the endopint to .php5 this will work.

 ![image](https://github.com/user-attachments/assets/15771b5c-be21-4dd4-aa0c-f6c43f649a5e)

  
3) fire up netcat and use an rev-shell launched from /uploads endpoint.
4) the user flag is in '/var/www' dir
5) for root flag we need priv-sec.

   `
        run 'find / -user root -perm /4000:'
   `
   
   `
        The above command is looking for a file with SUID permissions that can be run as root.
   `
   
   `
        Find for the service whose permission is not denied.
   `
   
   `
        /usr/bin/python can be used for priv-esc.
   `
   
7) Visit 'gftobins' and search for python and use the command under SUID. Baam!!! You are root now.

   ![image](https://github.com/user-attachments/assets/69ff531d-7ce7-4c77-ac64-0a0c27805c0d)
  
8) navigate to /root to read the root.txt
