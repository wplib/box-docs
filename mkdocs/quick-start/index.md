title: Quick Start
# WPLib Box Quick Start

1. [==Download==](/download/) the latest WPLib Box.

2. Download and install ==[**VirtualBox**](https://www.virtualbox.org/wiki/Downloads)== and 
   then ==[**Vagrant**](https://www.vagrantup.com/downloads.html)==<br> 
   _(in the near future WPLib Box will not require Vagrant.)_

3. ==Unzip== WPLib Box into a new project directory,<br>use `~/Sites/example.local` or 
`C:\Sites\example.local` for this quick start.

4. ==Open== a [terminal/command prompt](/how-to/tutorials/terminal.md)<br>
   _(in the near future WPLib Box won't require you to use the command line.)_
   
5. ==Change== to your project directory, i.e. 
    
    **MacOS or Linux**     
    
        cd ~/Sites/example.local
    
    **Windows**     
    
        cd C:\Sites\example.local
    
6. ==Type== the following command:
    
        vagrant up
    
7. _When prompted_ ==enter your password== for your Mac, Windows or Linux [host computer](/glossary#host-machine)<br>
_(or skip this step and [manually add entries](/how-to/tutorials/host-entries.md) for `example.local` to `/etc/hosts`)_

8. ==Open `project.json`== in your text editor and change the line:

        "hostname": "box.local",
   
       To:

        "hostname": "example.local",
    
9. Now ==visit== `http://example.local` in your browser. 
         
10. That's it, you are ==now experiencing WPLib Box!== :-)

----

P.S. Don't forget to ==[Join our Slack](https://launchpad.com/wplib)== to ask any questions you may have.
     
