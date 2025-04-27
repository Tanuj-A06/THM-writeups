Start the machine and navigate to the web-page

We are provied with the hint in the decription of the room.

![image](https://github.com/user-attachments/assets/a54d65f4-6313-4ecb-987c-479df7b9dca8)

The web=page:

![image](https://github.com/user-attachments/assets/24915067-a945-4a8c-8119-99d259be2bda)

Via 'Discography' we notice someting intresting:

![image](https://github.com/user-attachments/assets/d5298dec-aa63-40ca-b0f6-b1073376f855)

Endpoint changes to '/?page='

We can exploit this.

Trying with input field with '/etc/passwd'

![image](https://github.com/user-attachments/assets/fbd16fd9-0cc7-4030-b4b8-f7c7322b5f23)

Looks like we are on right track, moving back a few directories with '../' we reach the root directory.

![image](https://github.com/user-attachments/assets/73f25d96-1d3e-4044-ac13-b7021971175f)

Bingo!!

Now changing the endpoint form '/etc/passwd' to '/flag.txt' we are greeted with the flag.

![Screenshot 2025-04-27 103002](https://github.com/user-attachments/assets/3d3abc07-b369-4655-a343-9cd170739a19)
