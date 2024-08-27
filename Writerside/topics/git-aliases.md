# git aliases
We can easily set up git aliases to make our git experience a bit simpler and faster.  
For example, we can configure our git to use ```git s``` to mean ```git status```.

There are two ways we can configure git aliases:
- Using the global .gitconfig file.
- Using the command line.

## Configuring aliases using global .gitconfig file
We can configure aliases and even configure git in general using the global .gitconfig file which is created for us at the time of installing git.  
In windows, the file is located in ```C:\Users\<your-username>\``` eg ```C:\Users\ADMIN\```.  
When you open this folder and look inside it, you will find the .gitconfig.  
In Unix-based systems, the file is located in ```~/.config/git/config``` or ```~/.gitconfig```.  
Open this file, it should look like so:  
![.gitconfig](gitconfig-file.png)

Let's configure an alias for ```git status``` to be ```git s```.  
Currently, if I run ```git s``` on my command line, I will get an error.  
![git s](git_s.png)

To do this configuration, we add [alias] field in the file and then below it, we do our mappings in the form alias=original.  
The indentation is optional but is good for readability.  
![configuring s for git status](git_s_config.png)

Now, when we run ```git s``` it should work fine.
![git s working](git_s_working.png)

## Configuring aliases using the command line
To configure aliases using the command line, we use the command:
```Bash
git config --global alias.YOUR_ALIAS ORIGINAL
```
for example, to configure ```git s``` to map out to ```git status```:
```Bash
git config --global alias.s status
```
![configuring alias on command line](configuring_alias_on_command_line.png)

## configuring aliases for commands that take in arguments
Some commands such as ```git commit -m MESSAGE``` take in an argument, in this case the message.  
In this case, no extra configuration is needed as git will pas these arguments for us.  
Let's configure ```git commit -m "MESSAGE"``` to simply be ```git c "MESSAGE"```

Right now the command won't work:  
![git c not working](git_commit_c.png)

Let's configure it:  
![configuring git c](git_c_config.png)

And now the command should work:  
![git c working](git_c_working.png)

