# Bandit Level 0
http://overthewire.org/wargames/bandit/bandit0.html

**SOLUTION**

This is a pretty simple level. It teaches us the usage of SSH command. So, what ssh command do is it create a secure, encrypted tunnel or connection between the client and server for remote login or access and file transfer between computer.

We got the required information from reading the instruction page.

**Host**: bandit.labs.overthewire.org

**Port**: 2220

**Username**: bandit0

**Password**: bandit0

The basic command structure of the ssh command that we need to look at for this level is the following: 

**ssh [username]@[server_address] -p [port]**

This leads to the following command:

**ssh bandit0@bandit.labs.overthewire.org -p 2220**

When the command is executed, the terminal prompts for a password. Entering the provided password (bandit0) grants access to the remote machine. Successfully logged into the Bandit server.

Since the task was only to log in, this concludes level 0


# Bandit Level 1
http://overthewire.org/wargames/bandit/bandit1.html

**SOLUTION**

Now, after log in from the bandit0 shell,  we land in the home directory from user ‘bandit0’. I can check this with the **pwd** command.

we have used the **'ls'** command to list the files in the current directory. We found the **readme** file. And now to read the password I have used the **'cat'** command. After using cat command the password for the ‘bandit1’ user is obtained.

<img width="752" height="202" alt="Screenshot 2026-04-24 193219" src="https://github.com/user-attachments/assets/f0f76568-71fa-4b8e-839b-5076ecde7157" />


# Bandit Level 2
http://overthewire.org/wargames/bandit/bandit2.html

**SOLUTION**

On the Bandit website it says that the password for the next level is stored in a file called **'**-**'**. So, we can't directly use the cat command on the file as the file is named -(hyphen). . If we directly use cat command, it won’t be able to understand that hyphen is a file name. So, we will use the command with the full path **[home/bandit1/-]**. This will help us to read the password stored as shown in the given figure. 


<img width="586" height="122" alt="Screenshot 2026-04-24 194636" src="https://github.com/user-attachments/assets/28e64b3b-c9cb-4862-bd54-605d290c2d24" />

So we got the next password.

