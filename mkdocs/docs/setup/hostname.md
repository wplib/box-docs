title: HOSTNAME

# Configuring WPLib Box's Domain Name

By default WPLib Box configures itself to load using the domain name `wplib.box`, 
assuming you allow it to update your [`hosts` file](/docs/tutorials/hosts-file/). But 
this is probably not the domain you want to use to work on your client's website.   

### Choosing a top-level domain for local use.
In _"early days"_ we local developers always used `.dev` for our local domains; e.g. `example.dev`. 
But [thanks to Google](https://medium.engineering/use-a-dev-domain-not-anymore-95219778e6fd) that 
is not really a good option anymore, especially if you ever plan to use Chrome.  

So let's say your client's website is `example.com`; we recommend you pick `example.local` _(because 
we like it!)_, or `example.test` since [.test](https://webdevstudios.com/2017/12/12/google-chrome-63/) 
is the shortest available name where the rug is not likely to be pulled out from under us in the future.  

### Changing the Domain Name

Assuming you stored your project in a subdirectory  named `example.local` of a `Sites` directory 
then to change WPLib Box's domain name is as simple as updating `HOSTNAME` in that project
directory, and then running `vagrant reload`:

**MacOS or Linux**
    
    cd ~/Sites/example.local
    echo example.local > HOSTNAME
    vagrant reload

**Windows**
    
    cd C:\Sites\example.local
    echo example.local > HOSTNAME
    vagrant reload

You can, of course, also load `HOSTNAME` into your IDE or text editor and change it that way too.