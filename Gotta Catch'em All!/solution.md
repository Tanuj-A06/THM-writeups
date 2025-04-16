Boot up the VM and run a nmap scan on the provide ip.

![image](https://github.com/user-attachments/assets/811fd424-c581-4958-97da-e76a2c723208)

We have port 80(http web page) and 22(ssh) available.

Visiting the web page we find:

![image](https://github.com/user-attachments/assets/11c3eb65-96fa-4a55-b749-88757f8df5f7)

A dfault apache page -_-, nevertheless, well see what we can find.

I find something very intesting on the web-page:

![image](https://github.com/user-attachments/assets/c33dd575-3f23-421e-9b4c-d019be1132d9)

This has no use on the web page, the given info doesen't have any functionality and is present there for a reason.

Trying it was username:password for 'ssh' login.

![image](https://github.com/user-attachments/assets/83397a20-97fc-4b30-a663-a6dc66917800)

Bingo!!! It worked.

``
Flag1: Grass-Type Pokemon
``

There is a zip file present in the Desktop directory,

![image](https://github.com/user-attachments/assets/82cd20a1-8174-4a66-b47d-ee2959f5de09)

Unzipping it and printing the grass type flag:

![image](https://github.com/user-attachments/assets/bd697dc3-0baa-4439-a48e-7233aea05ee8)

The flag is present in a hexadecimal form, decoding it we get the flag:

![Screenshot 2025-04-16 210307](https://github.com/user-attachments/assets/0eece56d-907a-4da5-b465-7d1e4f36ea4c)

``
Flag2: Water-Type Pokemon:
``

Running the script the find the water type ``find / -name water-type.txt 2> /dev/null`` Explanation: Start finding from / i.e root dir and find for perticular file name. '2>/dev/null' to supress any errors. We find the file:

![image](https://github.com/user-attachments/assets/50086ff8-d68e-4767-bb9b-662d96b12eb6)

![image](https://github.com/user-attachments/assets/ae327b96-5d35-4e49-bb8e-91eaa294e334)

Its a rot cipher, dcoding it we get the flag.

``
Flag3: Fire-Type Pokemon:
``

Doing the same as water type we find the 3rd flag too:

![image](https://github.com/user-attachments/assets/0f08d27c-fabd-4130-8069-d0e0ff8dd5c6)

We get a base64 encoded string, dcoding it we get the flag:

![image](https://github.com/user-attachments/assets/54dce0f4-1fee-4e32-bac5-528198e974c2)

``
Root flag:
``

Usual priv-escalation scripts didn't work(sadly) but i found something intresting.

![image](https://github.com/user-attachments/assets/1d9b7904-d5d6-42d9-931f-80cd6410dca5)

This contians the username:password for getting root level permissions.

There is the final flag in /home directory:

![image](https://github.com/user-attachments/assets/52cd7228-9946-4dcd-893a-a86d3bc45116)
