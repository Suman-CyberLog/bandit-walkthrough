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

The password for the next level is stored inside a file named spaces in this filename. So, we use the **ls** command. In order to read files with spaces in the name you have to put the file name in quotation marks. We ran **cat ./"spaces in this filename"** and received the next password:

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

Now if we are to use the **cat** command our screen would be filled with unreadable mesh. So, first, we need to distinguish human-readable strings in ‘data.txt’. We use the **strings** command. And to get to the exact location of the password, we are going to use grep. Since the task was unspecific regarding the number of equal signs, I used 3. 

<img width="553" height="116" alt="Screenshot 2026-04-29 210424" src="https://github.com/user-attachments/assets/be3448de-d991-44cf-9ff3-9dc3e0a49493" />

This gives us the password for the next level. 


# Bandit Level 10 → Level 11
http://overthewire.org/wargames/bandit/bandit11.html

**SOLUTION**

The password for the next level is stored in the file data.txt, which contains base64 encoded data.

We can read the file using the **cat** command and **decode** the Base64 ourselves, but there's a Linux command that can handle this for us. We use piping to combine the **cat** command and the **base64** command with the **d** parameter to read and decode the text at the same time. 

<img width="747" height="115" alt="Screenshot 2026-04-29 210656" src="https://github.com/user-attachments/assets/c8f84fa5-af5a-40e0-b52e-5e2698ae50b2" />

This gives us the password for the next level.


# Bandit Level 11 → Level 12
http://overthewire.org/wargames/bandit/bandit12.html

**SOLUTION**

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

The data.txt file contains 1 line that was encrypted with the ROT13 algorithm.Many websites provide ROT13 encryption and decryption, but unfortunately, Linux does not have a built-in ROT13 command.So, I utilized the **tr** command for substitution. This command translates characters depending on the parameters provided - A->N,…,Z->M.

<img width="722" height="103" alt="image" src="https://github.com/user-attachments/assets/876b4613-59b0-4203-a366-72c081b455b9" />

This gives us the password for the next level.


# Bandit Level 12 → Level 13
http://overthewire.org/wargames/bandit/bandit13.html

**SOLUTION**

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.  For this level it may be useful to create a directory under /tmp in which you can work using mkdir. Then copy the datafile using cp, and rename it using mv.

<img width="651" height="132" alt="image" src="https://github.com/user-attachments/assets/81582c5f-586b-4bd2-b013-38c9e3e02d73" />

Now to understand the type of file we are going to use the file command it returns us the type of file. On running the command, we are informed that the file is ASCII text.The xxd command in Linux creates a hexdump of a file. It can also reverse this process. We will use it to get back the original file. We will use the **'r'** option to reverse the process and specify a filename for the output. We will call it **data1**. Now, let's verify the retrieved file by using the file command once more. This indicates that it is a **gzip compressed file**.

Next, we need to decompress it. First, we will rename the file to give it the correct **gzip** extension. We will use the move command for this purpose. The file has been renamed to **data2.gz**. Now, we will use the gzip command with the **-d** option to decompress the file.

Now it's time to verify the retrieved file, so we use the file command once more. This indicates that it is a **bzip2 compressed file**.

Next, to decompress it, we must rename the file and give it the correct **bzip2 extension**. We will use the move command for this purpose. We renamed the file to **data3.bz2**. Now, we will use the bzip2 command with the **-d** option to decompress the file.

Again we will check the retrieved file by using file command. This shows us that it is a **gzip compressed file**.

 we need to rename the file and assign it the appropriate **gzip extension**. We will use the move command for this as well. We renamed the file to **data4.gz**. Now, using the gzip command with the -**d** parameter, we decompress the file.

We again use the file command to check the retrieved file and now it is a tar archive file.


 <img width="825" height="530" alt="image" src="https://github.com/user-attachments/assets/2e482b16-4d96-4c6c-a1af-8d8bd7ac5270" />


To extract the files, we will utilize the **tar** command with the -**xf** options (where -x = Extract files from an archive and -f =Use the following archive file). This will result in a file called **data5.bin**. 

we use the file command again to check the retrieved file. To extract the files, we will use the **tar** command with the **-xf** options. This will result in a file called **data6.bin**. 

Again running file command on the retrieved file and this time it is a bzip2 compressed file. Now using the **bzip2** command and **-d** parameter, we decompress the file named **data6.bin.out**.

and again checking the retrieved file with file command and now it is a tar archive file. 

To extract the files, we will utilize the **tar** command with the -**xf** options . This will result in a file called **data8.bin**.

We again use the file command to check the retrieved file and now it is a gzip compressed file. 

we need to rename the file and assign it the appropriate **gzip extension**. We will use the move command for this as well. We renamed the file to **data9.gz**. Now, using the gzip command with the -**d** parameter, we decompress the file. 

<img width="976" height="595" alt="image" src="https://github.com/user-attachments/assets/3fbe0c17-7052-48cb-8af4-42accedc2567" />

Now, on running the  file command on the **data9** file , we are informed that the file is ASCII text. This could be a readable file. We use the head command to access the file.

<img width="532" height="87" alt="image" src="https://github.com/user-attachments/assets/20335466-46cd-4e6f-9202-da3a467fe26e" />

This gives us the password for the next level. 


# Bandit Level 13 → Level 14
http://overthewire.org/wargames/bandit/bandit14.html

**SOLUTION**

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don�t get the next password, but you get a private SSH key that can be used to log into the next level. 

When I logged into the machine, we saw **sshkey.private** file using the **ls** command. Now that we know where the file is located, we can move it to my machine.
We have used  scp to connect to the remote machine and get the ssh key.

<img width="797" height="255" alt="Screenshot 2026-05-02 200145" src="https://github.com/user-attachments/assets/7858d712-e9d1-4fda-9535-6555e63953b7" />


Now, we have the sshkey.private in our machine.  we have to change its permission using **chmod** command. So, why are we changing the permission  it's because SSH checks the security of your private key file. If the file is accessible by others except owner (like permissions 644 or 777), SSH will refuse to use it.

After changing the permission to 600. we can use the sshkey.private file in ssh command. 


<img width="636" height="337" alt="image" src="https://github.com/user-attachments/assets/da9e44d7-72e4-4e7a-93d5-b5cac2e469c2" />


And we got into the server as bandit14. We can also check the password for bandit14 by using cat command path of the password file.

<img width="697" height="55" alt="image" src="https://github.com/user-attachments/assets/6fee7509-0c38-4396-9e8a-2f493548f193" />

This gives us the password for the next level.

# Bandit Level 14 → Level 15
http://overthewire.org/wargames/bandit/bandit15.html

**SOLUTION**

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Based on the hint, we need to connect to port 30000 on localhost and then submit the password of this level to that same port.To achieve this, I used "netcat localhost 30000" and after confirming the connection, I pasted the password for bandit14. 


<img width="777" height="78" alt="Screenshot 2026-05-02 200748" src="https://github.com/user-attachments/assets/01836934-e513-4573-8571-c0aa3394b423" />

This gives us the password for the next level.

# Bandit Level 15 → Level 16
http://overthewire.org/wargames/bandit/bandit16.html

**SOLUTION**

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Because the challenge says we can get the password by using SSL encryption, I'm going to connect to the local server using the OpenSSL client and send the password of the current level. After that, the server will send back the password needed for the next stage.

<img width="685" height="233" alt="Screenshot 2026-05-02 212310" src="https://github.com/user-attachments/assets/30d4c775-19b7-4ff0-938e-31a27f938ec6" />
<img width="685" height="112" alt="Screenshot 2026-05-02 212337" src="https://github.com/user-attachments/assets/e8ff4d94-c954-4022-b087-c25fdf61e800" />


This gives us the password for the next level.

# Bandit Level 16 → Level 17
http://overthewire.org/wargames/bandit/bandit17.html

**SOLUTION**

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

To start, we should identify the open ports from 31000 to 32000 on localhost and see what services are running on those ports. To do this I ran the **nmap** command with **-sV** flag for localhost on the above mentioned port range , to see the open port and the version of the services.

<img width="741" height="181" alt="Screenshot 2026-05-04 223219" src="https://github.com/user-attachments/assets/df9a146b-72fd-40cb-be97-bb7c2456c998" />

As we can see, there are five open ports. Out of these, only two ports (31518 and 31790) are utilizing SSL. Port 31518 is running the echo service and port 31790 runs an unknown service ,which seems quite promising. So, We are now using OpenSSL  with -**ign_eof**, (which means Ignore End of the file so with this flag  the connection stays open and we receive the output properly).


<img width="646" height="138" alt="Screenshot 2026-05-03 210913" src="https://github.com/user-attachments/assets/f6779687-0fae-4735-8364-7d7bd3149f56" />
<img width="646" height="228" alt="Screenshot 2026-05-03 211015" src="https://github.com/user-attachments/assets/5aada543-75c2-4fbd-89a4-20a956bb62dc" />

After running the command and sending the password we have received a private SSH key. We start by creating a file with the vim editor, which I named 'bandit17.key', to store the key. Next, we modify the file's permissions to make it read-only for the current user by using the chmod command. 

<img width="662" height="119" alt="Screenshot 2026-05-03 211046" src="https://github.com/user-attachments/assets/10055a8c-58c8-434e-af53-69e6f21ee30a" />
<img width="662" height="44" alt="Screenshot 2026-05-03 211105" src="https://github.com/user-attachments/assets/36894603-e4a8-4500-b735-038d134473cb" />


Finally, we use ssh along with the private key to connect to level 17.


# Bandit Level 17 → Level 18
http://overthewire.org/wargames/bandit/bandit18.html

**SOLUTION**

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

I was already logged into the bandit17 in the previous level. Now i have checked the file using **ls** command i.e. passwords.old and passwords.new. I ran "diff password.new passwords.old" and since I placed 'passwords.new' in the first position, the new password is printed in that same first part.

<img width="791" height="167" alt="Screenshot 2026-05-03 211336" src="https://github.com/user-attachments/assets/e1253bab-0cba-48de-8d33-10b3b0563963" />

# Bandit Level 18 → Level 19
http://overthewire.org/wargames/bandit/bandit19.html

**SOLUTION**

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

The file '.bashrc' is running each time a terminal is initiated. Consequently, it is also runnig during SSH logins. SSH not only allow us to access a machine remotely, but it also facilitates the remote execution of commands after the common SSH expression.

First, we use **ls** to confirm that the 'readme file' is present in the folder, and then we can use **cat** to view its contents.

<img width="687" height="507" alt="Screenshot 2026-05-05 182149" src="https://github.com/user-attachments/assets/cd28415a-7f72-44e2-88d2-47a1a8481e03" />


This gives us the password for the next level. But we can **"alternatively"** use different method to do the same  by  using a command using SSH, but with the **-t** flag. This enables a ‘pseudo-terminal’ to operate on the target machine, allowing us to run **\bin\sh**. This method is particularly beneficial when we need to run several commands, as it eliminates the need to repeatedly enter the SSH statement and password.

<img width="739" height="326" alt="Screenshot 2026-05-05 181824" src="https://github.com/user-attachments/assets/d60ecfb7-e57a-4685-8082-9211f7569923" />

This will also give us the password.

# Bandit Level 19 → Level 20
http://overthewire.org/wargames/bandit/bandit20.html

**SOLUTION**

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

After logging into bandit19's profile, I executed the command "**ls**" and discovered a binary file called "**bandit20-do**". The hint indicated that I should run the file, so I proceeded with the command "**./bandit20-do**". The output displayed, "Run a command as another user. Example: ./bandit20-do whoami". Following that, I executed "**./bandit20-do id**" and was able to view the id information for bandit20. The script appeared to function as described, allowing me to "run a command as another user".

<img width="1276" height="201" alt="Screenshot 2026-05-05 183825" src="https://github.com/user-attachments/assets/1fb59f98-ec7b-4599-a94e-da5d3b888889" />


Then I check who the owner of the setuid binary is using **ls -l** command. the owner is bandit20 and the group is bandit19. The permission set ‘**-rwsr-x—**’ indicates that the user bandit19 has the ability to execute the binary, but it runs under the identity of user bandit20.

This means that when the file is run, it will operate as bandit20. The passwords for all levels can be found in the directory /etc/bandit_pass/, although each password file is configured with read and access permissions limited to the user of the corresponding level only. To retrieve the key for level 20, use the bandit20-do executable to access the bandit20 password file.

<img width="580" height="57" alt="Screenshot 2026-05-05 183921" src="https://github.com/user-attachments/assets/0c679328-5ad9-4645-b0ca-cd0d3d704428" />

This give us the password for the next level.

# Bandit Level 20 → Level 21
http://overthewire.org/wargames/bandit/bandit21.html

**SOLUTION**

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

After logging in, I can see an executable named suconnect in the home directory. To run this,we will utilize the two terminal screen. In the first terminal, we can establish a connection in server mode with '**netcat**', which will listen for incoming connections. To have netcat transmit the password, I will use **echo** and pipe it into netcat. The **-n** flag is included to avoid newline characters in the input. Finally, we will let the process run in the background by using **&**.

<img width="1777" height="380" alt="Screenshot 2026-05-05 191131" src="https://github.com/user-attachments/assets/e4e45073-c357-4443-a7b4-a0bd268c5b9c" />

In the second terminal, execute the suconnect file with port 1234, which will connect to our netcat server, receive the password provided through echo, and return the next password.

# Bandit Level 21 → Level 22
http://overthewire.org/wargames/bandit/bandit22.html

**SOLUTION**

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Based on the hint, there's a configuration for a cron job located in "/etc/cron.d/" that will assist us in completing this level. Cron is a program that executes a specific command or script at designated times or intervals. When I navigated to the "/etc/cron.d/" directory and executed "**ls**", I noticed several files, but I figured we should focus on the file named "cronjob_bandit22".

 I ran "cat /etc/cron.d/cronjob_bandit22" to check what the cron job was doing, and I discovered that the script located at /usr/bin/cronjob_bandit22.sh is executed by the bandit22 user. The five asterisks signify that it runs every minute, every day. To know what exactly is executed, we need to take a look at the bash file. 

 This script generates a file in the 'tmp' directory and grants read access to all users. It then transfers the contents of the bandit22 password file into the newly created file.

 Therefore, the password for the next level can be found in this generated file:

 <img width="1046" height="262" alt="Screenshot 2026-05-07 200934" src="https://github.com/user-attachments/assets/69d08d63-5e95-47d8-878c-24850a348eae" />


# Bandit Level 22 → Level 23
https://overthewire.org/wargames/bandit/bandit23.html

**SOLUTION**

After logging in, head over to /etc/cron.d/ to review the listed files. Use the cat command to display cronjob_bandit23. You'll see that it schedules a specific shell script to run as the user bandit23. 

Next, display the contents of the shell script. The first variable is 'myname', which captures the output from the whoami command. Since this script runs as bandit23, the whoami command will return 'bandit23'. Therefore, the final line indicates that the password for bandit23 will be saved in a file located in the '/tmp' directory. 

The filename is generated by the command echo I am user $myname | md5sum | cut -d ' ' -f 1. We just need to replace $myname with bandit23, run it, and the output will give us the filename.

<img width="875" height="556" alt="Screenshot 2026-05-10 194356" src="https://github.com/user-attachments/assets/ac125f90-54ec-4958-a1d4-c09d9af0c154" />

# Bandit Level 23 → Level 24
https://overthewire.org/wargames/bandit/bandit24.html

**SOLUTION**

After logging in, navigate to /etc/cron.d/ to check the cron configuration files. Use the **cat** command to show the contents of the bandit24 cron file. You’ll see that a shell script is set to run every minute as the user bandit24.

Next, take a look at the shell script's contents. The script changes to the /var/spool/bandit24/foo directory and runs every file located there. Since the cron job operates under the bandit24 user, any script placed in this directory will execute with bandit24's privileges.

<img width="770" height="497" alt="Screenshot 2026-05-13 102807" src="https://github.com/user-attachments/assets/c456d008-95b1-43cd-a9da-024d2edd26d4" />

To take advantage of this, create a temporary directory in /tmp and write a shell script that retrieves the password stored in /etc/bandit_pass/bandit24. Redirect the output to a file in your temporary directory and change its permissions to ensure it can be read later.

<img width="707" height="71" alt="image" src="https://github.com/user-attachments/assets/dcd38d82-cba4-4d18-9ca9-c8762754c243" />
<img width="550" height="61" alt="image" src="https://github.com/user-attachments/assets/c38ac27d-1b85-413f-a1de-0bc5a8ce5f1f" />

Make the script executable with chmod +x and copy it to /var/spool/bandit24/foo/. The cron daemon will automatically run the script within a minute.

<img width="745" height="18" alt="image" src="https://github.com/user-attachments/assets/0f5e1431-2bc7-4d80-9306-059c69b5f0d1" />

After the cron job executes, check the contents of the password file in your temporary directory. The output will display the password for bandit24.

<img width="526" height="104" alt="image" src="https://github.com/user-attachments/assets/58beb366-b379-4a72-ae70-ff9360178cd8" />

The output will display the password for bandit24.


