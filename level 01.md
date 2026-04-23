# Bandit Level 0
Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

SOLUTION
This is a pretty simple level. It teaches us the usage of SSH command. So, what ssh command do is it create a secure, encrypted tunnel or connection between the client and server for remote login or access and file transfer between computer.

We got the required information from reading the instruction page.

Host: bandit.labs.overthewire.org

Port: 2220

Username: bandit0

Password: bandit0

The basic command structure of the ssh command that we need to look at for this level is the following: 

ssh <username>@<server> -p <port>

This leads to the following command:

ssh bandit0@bandit.labs.overthewire.org -p 2220

When the command is executed, the terminal prompts for a password. Entering the provided password (bandit0) grants access to the remote machine. Successfully logged into the Bandit server.
