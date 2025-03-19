Download the task-files:

'strings' command tells us that the executable checks for password.

![image](https://github.com/user-attachments/assets/dde44fea-b29c-4474-af32-734904e21d44)

radare is dissabled and we can't read it.

![image](https://github.com/user-attachments/assets/566f311b-2af2-478c-8b88-158643469641)

Check out why we are unable to read the executable:

run 'file' to check out what kinde of executable it is:

![image](https://github.com/user-attachments/assets/a52cc9cd-7051-4917-8fdb-cf98bf8e739a)

We are met with a very specific problem:
``ELF 64-bit MSB *unknown arch 0x3e00* (SYSV)``

A simple google search leads to an stackoverflow discussion, we need to edit the hex of the file and make it match this:
![image](https://github.com/user-attachments/assets/fb546e46-debd-4e94-aed7-33fb138d371b)


``
        Ennable the redablity for the executable.
``

copy the file for further investigations. 

i) hexeditor:
  
Edit out the 6th byte from whatever it is to '01'
          
This will enable the file to be redable in radare (This is only problem specific might not work for other problems, but still worth a try ;))
                
ii) Read the file with 'r2 -d' and navigate to the 'main':
  
Here look for the strings passed through the function (They were present in the comments).

![Screenshot 2025-03-19 223808](https://github.com/user-attachments/assets/38970c0a-f457-4756-a294-115fcfc46735)

          
Re-assemble the broken strings into 1 whole string. Use it to check if correct.

![Screenshot 2025-03-19 224127](https://github.com/user-attachments/assets/5364d885-09cb-4520-9437-eb649e95f885)
          
Use the re-assembled string and wrap it around in 'THM{}'
