title: Glossary

# Glossary of Terms related to WPLib Box

When working with a new tool you can often be overwhelmed by new jargon. 
While WPLib Box is unfortunately no different our vision is to empower
you to understand everything you need to know to use WPLib Box effectively, 
such as this glossary.  

## Important Terms 

The following are terms are some of the ones we use in our documentation, although they are certainly not all. 

!!! note 
    We are defining these terms as they related to WPLib Box. Thus our definitions may differ somewhat 
    from more the general definitions such as those you might find on Wikipedia.   

### Host Machine

 The ==Host machine== is your physical computer that typically runs Windows, Mac or Linux, and that _"hosts"_ WPLib Box 
 similar to how your computer hosts a Microsoft Word document or an Apple Keynote presentation.

### Virtual Machine

 A ==Virtual Machine== is a full Linux operating system that runs _"virtually"_ within your Windows, 
 Mac or Linux [host computer](#host-machine).  
 
 
 Or more clearly, a bit-for-bit image of what could have been a physical computer's file system to enable 
 _emulation_ of that _"computer"_ using [VirtualBox](#virtualbox) running _within_ your _"Host"_ computer.  

### VirtualBox

 ==[**VirtualBox**](https://www.virtualbox.org/)== is open source software &mdash; recently acquired by 
 [Oracle](https://www.oracle.com/) &mdash; that is required by WPLib Box to enable the Linux virtual 
 machine to run in your host Windows, Mac or Linux computer.   

### Guest 

 The WPLib Box ==Guest== is the Linux-based [virtual machine](#virtual-machine) running within 
 your [host machine](#host-machine).

### _(Software)_ Stack

 The WPLib Box ==(Software) Stack== is the collection of software used by WPLib Box to perform its job for you. 
 
 To host WordPress in WPLib Box your local development stack consists of a web server like Nginx or Apache, 
 a database server like MySQL or MariaDB, a version of PHP such as 5.6 or 7.2 and possibly a cache server 
 like Memcached or Redis.
 
 To learn more about [WPLib Box Stacks](/architecture/stacks/), click the link.

 For a more general purpose definition of _"[Software Stack](https://en.wikipedia.org/wiki/Software_stack)"_ 
 click the link to see what Wikipedia has to say. 
 
### Provisioning

 ==Provisioning== is the process of installing and configuring the [software stack](#software-stack) 
 on WPLib Box prior to your first use of WPLib Box. 

 Provisioning includes tasks like importing an initial WordPress database from `/sql/provision.sql` and adding 
 permissions to the same database. 

### Components

 ==Components== in the context of WPLib Box are packages of software that collectively comprise 
 your WPlib Box's [software stack](#software-stack). 
 
 A _component_ can be a [container](#containers), a script, source code, or various other types of files. 
 To learn more details about [_WPLib Box Components_](/architecture/components/), click the preceding link.

### Containers
==Containers== in the context of WPLib Box are used to package each [service and executable](/architecture/components/#categories)
[component](#components) in its own sandbox to effectively eliminate the most common conflicts that occur 
between services and executables, and to be more flexible in terms of which services and executables can 
be incorporate into a project's [software stack](#software-stack). 
 
WPLib Box strives to use **individual** [Docker containers](https://www.docker.com/what-container) for all 
service and executable components it needs. This [architecture](/architecture/) decision is in large part 
why WPLib Box is more powerful and more flexible than any other local development solution for WordPress today.

This architecture also empowers WPLib Box to more quickly support newer versions of services and executables, 
often enabling you &mdash; the WPLib Box user &mdash; to upgrade to a new version in the case we have not yet
updated our official containers.      
 
### Box Image

 A ==Box Image== is a digital file containing the binary bits of WPLib Box's [virtual machine](#virtual-machine). 
 
!!! note 
        The box image format used by WPLib Box has been defined by [Hashicorp](https://www.hashicorp.com/)'s 
        [Vagrant](#vagrant). 
 
WPLib Box's box image has been pre-[provisioned](#provisioning) with the [WPLib Box software stack](#software-stack) 
 beyond what the default Linux distribution provides which is why in-part WPLib Box is so easy to get started 
 _(when compared to other solutions like [VVV](https://varyingvagrantvagrants.org/).)_ 
  
 You can see [the history of _(most)_ WPLib Box images](https://app.vagrantup.com/wplib/boxes/wplib) at 
  Hashicorp's [VagrantCloud](https://vagrantcloud.com) repository of Vagrant images available for download.
  
!!! note "Note"
      We say _"most"_ WPLib Box images because [when Hashicorp moved](https://www.hashicorp.com/blog/vagrant-cloud-migration-announcement)
      from its old [_"Atlas"_ repository](https://www.hashicorp.com/blog/atlas-announcement) to
      the current VagrantCloud they neglected to transfer over some of our historical releases and thus 
      they have been lost to the mists of time.   
 
 WPLib Box's _current_ box image is based on [Ubunutu](https://www.ubuntu.com/), but we will soon be replacing it 
 with a more streamlined Linux distribution.  
  
### Vagrant

 ==[**Vagrant**](https://www.vagrantup.com/)== is software currently required by WPLib Box that reads a configuration 
 file named [`Vagrantfile`](#vagrantfile) in your WordPress project's directory and it automates the creation 
 and configuration of a [virtual machine](#virtual-machine) that is run using [VirtualBox](#virtualbox).
 
 Vagrant is software written in [the Ruby programming language](https://www.ruby-lang.org) and it reads information 
 from a `Vagrantfile` found in your project's directory on your [host computer](#host-machine) and 
 it uses that information to download and configure WPLib Box.
   
!!! note
    We plan to eliminate the need to use Vagrant in the very near future. At that point WPLib Box will only be 
    dependent on [VirtualBox](#virtualbox).

### Vagrantfile

 A ==`Vagrantfile`== is a specialized [Ruby language](https://www.ruby-lang.org) script that is run by [Vagrant](#vagrant) 
 to automate the setup of WPLib Box. 

 Although a Ruby script, `Vagrantfile` is [declarative](https://stackoverflow.com/a/1619853/102699) in nature &mdash; 
 more like a `JSON` file &mdash; as it was designed to allow you to _"declare"_ the details needed by Vagrant to 
 automate the creation and configuration of your [virtual mahine](#virtual-machine) using [VirtualBox](#virtualbox).
    
 The _"declarations"_ in the `Vagrantfile`  tell Vagrant what it needs to know to:
  
 1. _(Initially)_ download the specified version of WPLib Box's [box image](#box-image) "_ into Vagrant's 
    [local box image cache](#local-box-image-cache) on your [host computer](#host-machine), 
 2. Set the IP address for the WPLib Box virtual machine,
 3. Add the host name used to reference WPLib Box  &mdash; e.g. `wplib.box` or  `example.local` &mdash; to your 
    host computer's [`hosts` file](#hosts-file),  
 4. [Mount](https://unix.stackexchange.com/a/3194/144192) your project directory on your host computer inside of 
    WPLib Box so PHP and Nginx/Apache can access them,
 5. Specify the username to be used for `vagrant ssh`; currently `boxuser` in WPLib Box's case and configure
    [SSH agent forwarding](https://developer.github.com/v3/guides/using-ssh-agent-forwarding/), 
 6. And finally, specify the _(lightweight, in the case of WPLib Box)_ scripts to run on `vagrant up`, both
    for initial install and subsequent uses.


### Hosts file
Your ==[`hosts` file](https://en.wikipedia.org/wiki/Hosts_(file))== is a plain text file found 
on your [host computer](#host-machine) that contains one of more IP addresses mapped to domain names. 

The purpose of your `hosts` file is to allow you to override the entries found at your DNS server. 
In the case of WPLib Box with `.local` domain names, your DNS server has no knowledge of your local 
development. This WPLib Box needs to add entries to your `hosts` file to allow you to use domain names 
for local development _instead of_ hard-to-remember ports and/or IP addresses; 
e.g. `http:/localhost:8888` or `http:/10.10.10.136`.  

Typically you at least have [`localhost`](https://en.wikipedia.org/wiki/Localhost) defined in your 
`hosts` file:

    127.0.0.1 localhost   
    
After WPLib Box is installed and configured[^1], your `hosts` file will look something like this _(likely 
with a different IP address and [Vagrant](#vagrant) hash.)_  The following enables     

    127.0.0.1 localhost
       
    10.10.10.136  wplib.box  # VAGRANT: c1906b61bcd8c3211d7426a8a3310413 (default) / 4fdce32d-d9b3-$
    10.10.10.136  docs.wplib.box  # VAGRANT: c1906b61bcd8c3211d7426a8a3310413 (default) / 4fdce32d-$
    10.10.10.136  www.wplib.box  # VAGRANT: c1906b61bcd8c3211d7426a8a3310413 (default) / 4fdce32d-d$
    10.10.10.136  adminer.wplib.box  # VAGRANT: c1906b61bcd8c3211d7426a8a3310413 (default) / 4fdce3$
    10.10.10.136  mailhog.wplib.box  # VAGRANT: c1906b61bcd8c3211d7426a8a3310413 (default) / 4fdce3$

??? info "A bit of `hosts` file history"
        Hosts files predate the Internet's Domain Name System (DNS) and were how early Internet users 
        mapped hostnames to IP addresses. This meant every user had to know the IP address of every 
        computer they wanted to visit on the internet, or at least the sysadmin for the computer needed 
        to know the IP address. Clearly that quickly became overwhelming for everyone on the Internet 
        and was why the DNS system was introduced.  
        

### Local Box Image Cache

 The term ==Local Box Image Cache== is a WPLib Box coined-term to name the **pristine** 
 [box image](#box-images) that [Vagrant](#vagrant) downloads to a local cache on your 
 [host computer](#host-machine) to enable quick cloning for additional projects. 
 
 `vagrant up` will clone a copy of this cached image into the [project box image](#project-box-image) 
 the first time it in run for a given [`Vagrantfile`](#vagrantfile), but running `vagrant destroy` 
 followed by a `vagrant up` will clone the cached box image too. 
 
 Your local box image cache [is located at](http://stackoverflow.com/a/10226134/102699):

- MacOS and Linux: `~/.vagrant.d/boxes`
- Windows: `C:\Users\{username}\.vagrant.d\boxes`

### Project Box Image

The term ==Project Box Image== is another WPLib Box coined-term to name the project-specific 
copy of the pristine copy [local box image cache](#local-box-image-cache) that [Vagrant](#vagrant) 
makes for each project in the following project-specific subdirectory: 


**Mac or Linux:**

    {project}/.vagrant  

**Windows:**

    {project}\.vagrant  

The upshot is if you `vagrant ssh` into a running Vagrant Box and make configuration 
changes those changes will be in the project box image, but not in the pristine copy of 
box image nor in other projects that share the same named Box Image. 

Beyond the project box image [VirtualBox](#virtualbox) will import these images into its own directory for 
each project: 

**Mac or Linux:**

    ~/VirtualBox VMs  

**Windows:**

    C:\Users\{username}\VirtualBox VMs

??? note "Why we plan to stop using [Vagrant](#vagrant)" 
    This extremely inefficent use of storage is but one of the many reasons we are planning to replace Vagrant with our own solution in the very near future. 

## Suggestions for Improvement
If you have any terms to add or suggestions for improvement to our existing descriptions we **welcome** your 
suggestions.  So please help out your fellow developers and [**fork this repo**](https://github.com/wplib/box-docs), 
make your fixes and then [**submit your pull request**](https://github.com/wplib/box-docs/pulls).


[^1]: Unless you have changed your host name in the `HOSTNAME` file, which you will almost certainly have done. 