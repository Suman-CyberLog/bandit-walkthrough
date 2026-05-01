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


# Bandit Level 0 → Level 1
http://overthewire.org/wargames/bandit/bandit1.html

**SOLUTION**

Now, after log in from the bandit0 shell,  we land in the home directory from user ‘bandit0’. I can check this with the **pwd** command.

we have used the **'ls'** command to list the files in the current directory. We found the **readme** file. And now to read the password I have used the **'cat'** command. After using cat command the password for the ‘bandit1’ user is obtained.

<img width="752" height="202" alt="Screenshot 2026-04-24 193219" src="https://github.com/user-attachments/assets/f0f76568-71fa-4b8e-839b-5076ecde7157" />


# Bandit Level 1 → Level 2
http://overthewire.org/wargames/bandit/bandit2.html

**SOLUTION**

On the Bandit website it says that the password for the next level is stored in a file called **'**-**'**. So, we can't directly use the cat command on the file as the file is named -(hyphen). . If we directly use cat command, it won’t be able to understand that hyphen is a file name. So, we will use the command with the full path **[home/bandit1/-]**. This will help us to read the password stored as shown in the given figure. 


<img width="586" height="122" alt="Screenshot 2026-04-24 194636" src="https://github.com/user-attachments/assets/28e64b3b-c9cb-4862-bd54-605d290c2d24" />

So we got the next password.


# Bandit Level 2 → Level 3
http://overthewire.org/wargames/bandit/bandit3.html

**SOLUTION**

The password for the next level is stored inside a file named spaces in this filename. So, we use the **ls** command. In order to read files with spaces in the name you have to put the file name in quotation marks. We ran " **cat "spaces in this filename**" " and received the next password:

<img width="500" height="92" alt="image" src="https://github.com/user-attachments/assets/02493a07-b8f1-4e55-a378-6f367294e784" />

# Bandit Level 3 → Level 4
http://overthewire.org/wargames/bandit/bandit4.html

**SOLUTION**

The password for the next level is stored inside a directory named inhere. So, we use the ls command  then "**cd**" to move into the inhere folder. After traversing inside inhere directory. we ran "**ls -a**", with the -a flag it shows all files, specifically also the hidden files. The hidden file is named ...Hiding-From-You. And after running **cat "...Hiding-From-You"**. We got the next password.

<img width="553" height="137" alt="image" src="https://github.com/user-attachments/assets/228ec10f-1639-4a51-b73d-baf530aad80b" />

# Bandit Level 4 → Level 5
http://overthewire.org/wargames/bandit/bandit5.html

**SOLUTION**

The password is stored in file inside the inhere folder, inside a **human-readable file**. After traversing inside inhere directory we run **ls** command. This shows us a bunch of files as shown in the image. We will use the file command to get the information about the files, to see which one is the human readable one. We can see that only **‘-file07’** is of type **‘ASCII text’**, which is one of the encodings, that humans can read.So, let’s read it using **cat** command.

<img width="781" height="376" alt="Screenshot 2026-04-27 212342" src="https://github.com/user-attachments/assets/6ea59160-a3d3-4056-b77a-869448dbee0b" />


This gives us the password for the next level. 


# Bandit Level 5 → Level 6
http://overthewire.org/wargames/bandit/bandit6.html

**SOLUTION**

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

a. human-readable<br>
b. 1033 bytes in size<br>
c. not executable

To start run **"cd"** into the inhere folder, After traversing inside inhere directory we run **ls** commandand noticed that there were a bunch of folder and inside those folders a couple of files. We will use the file size to find the file (**find . -size 1033c**) in which we have to use ‘c’ for depicting size in bytes. From this command we got to know that the password is stored in file2. So, let’s read it using **cat** command.

<img width="805" height="141" alt="Screenshot 2026-04-28 215904" src="https://github.com/user-attachments/assets/c7ca270c-7e5a-4a96-8940-bc665be324dc" />

This gives us the password for the next level.

# Bandit Level 6 → Level 7
http://overthewire.org/wargames/bandit/bandit7.html

**SOLUTION**

The password for the next level is stored somewhere on the server and has all of the following properties:

a. owned by user bandit7<br>
b. owned by group bandit6<br>
c. 33 bytes in size

The **find** command can be used to find files on the server. Running the command **find / -type f -user bandit7 -group bandit6 -size 33c**. However, it will also print a Permission denied error for files that we do not have permission. So, we have to used 2>/dev/null to hide the error messages. Now as we can see in the given image, we successfully located the password file hidden over the server. So, let’s read it using **cat** command.

<img width="772" height="165" alt="image" src="https://github.com/user-attachments/assets/52e385e5-64c9-42ca-a554-68314d43f3cb" />

This gives us the password for the next level.

# Bandit Level 7 → Level 8
http://overthewire.org/wargames/bandit/bandit8.html

**SOLUTION**

The password for the next level is stored in the file data.txt next to the word millionth.

we use the **ls** command. We are hinted that the password isi next to the word millionth. We are going to use the **grep** command for finding millionth. Here we using the (**|**), that pipe the output of **cat** to **grep** as input to look through a text file. In our case, first cat command reads the file and then the data inside the file is sent to grep command to work on.

<img width="537" height="98" alt="Screenshot 2026-04-29 205555" src="https://github.com/user-attachments/assets/2865094a-7f81-4704-ab6b-c4cbb460a1c4" />

This gives us the password for the next level.


# Bandit Level 8 → Level 9
http://overthewire.org/wargames/bandit/bandit9.html

**SOLUTION**

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

To find the line that occurs only once in the file. We first sort the text inside the data.txt file, and then filter for the unique one.

<img width="596" height="108" alt="Screenshot 2026-04-29 205840" src="https://github.com/user-attachments/assets/1b79d594-5fe2-4300-96e1-a35eb5f7eb5a" />

This gives us the password for the next level.


# Bandit Level 9 → Level 10
http://overthewire.org/wargames/bandit/bandit10.html

**SOLUTION**

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

