title: Secure Shell

# SSH - [Secure Shell](https://www.ssh.com/ssh/protocol/)
`SSH` stands for _"==Secure Shell=="_ and is the standard means of managing a Linux-based 
computer that is not your [host computer](/glossary#host-machine).  Typically this means a _remote_ computer, but as WPLib 
Box runs inside of your host computer then calling it a _"remote"_ computer would be a misnomer, but the principle is the same. 

Said another way, SSHing into a computer is a way to gain access to running commands at a command line for that computer 

!!! info "SSH in Modern Culture" 
    Secure Shell is all the rage for hacker movies and TV shows like [Mr. Robot](https://www.youtube.com/watch?v=PGjLhOhMLXc).  
 
## SSHing into WPLib Box
Depends on your host computer's operating system you access SSH slightly differently:

- On Windows [open your command prompt](https://www.lifewire.com/how-to-open-command-prompt-2618089), 
- On MacOS [open terminal](https://www.wikihow.com/Open-a-Terminal-Window-in-Mac), 
- Or if Linux is your host computer, you know how to do this.

Once you have access to a terminal prompt type the following commands:

### MacOS or Linux     

    cd /path/to/your/project
    vagrant up
    vagrant ssh

### Windows     

    cd c:\path\to\your\project
    vagrant up
    vagrant ssh


## Commands Explained
In case you are new to terminal: 

1. `cd` changes what you host computer thinks is your _current_ directory to that of your 
 WordPress project's directory, 
2. The `vagrant up` command makes sure your WPLib Box virtual machine is running for your project, and 
3. The `vagrant ssh` command requests to enter your project's WPLib Box with a command prompt available.  


## On Success:
If you are successful, your screen should look like this:

![SSHing into WPLib Box](/images/secure-shell.png)
 
 
