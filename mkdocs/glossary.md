title: Glossary

# NOT COMPLETE
## Glossary of Terms related to WPLib Box

When working with a new tool you can often be overwhelmed by new jargon. 
While WPLib Box is unfortunately no different our vision is to empower
you to understand everything you need to know to use WPLib Box effectively, 
such as this glossary.  

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

### Provisioning

 ==Provisioning== is the process of installing and configuring the [software stack](#software-stack) 
 on WPLib Box prior to your first use of WPLib Box. 

 Provisioning includes tasks like importing an initial WordPress database from `/sql/provision.sql` and adding 
 permissions to the same database. 

### Components

 ==Components== in the context of WPLib Box are packages of software that collectively comprise 
 your WPlib Box's [software stack](#software-stack). 
 
 A _component_ can be a [container](#containers), a script, source code, or various other types of files. 
 To learn more details about [_WPLib Box Components_](/docs/architecture/components/), click the preceding link.

### Containers
==Containers== in the context of WPLib Box are used to package each [service and executable](/architecture/components/#categories)
[component](#component) in its own sandbox to effectively eliminate the most common conflicts that occur 
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

### Site Builder
Here at the WPLib Box team we define a _"Site Builder"_ as someone who installs WordPress, plugins, and themes 
&mdash; who might tweak the HTML, CSS, JS or PHP from time to time &mdash; but for the most part is not and 
does not consider themselves a _"programmer."_ 

We **love** professional Site Builders and think they provide an invaluable service to their clients so we 
are just as excited to hear from site builders how we can make WPLib Box better to help them their do their 
jobs as we are to hear from front-end or even backend WordPress developers.  

### Front-end Developer
Here at the WPLib Box team we define a _"Front-end Developer"_ as someone who minimally has HTML and CSS 
skills &mdash; especially for responsive design &mdash; and who may or may not have Javascript programming 
skills and/or front-end build system skills combined with a CSS preprocessor like SASS or LESS. In our experience
front-end development and theme development go hand-in-hand, although front-end developers can be found building 
plugins as well. 

And we **love** professional front-end developers as without them WordPress sites would never be as compelling 
nor as functional as so many WordPress sites and themes have become. So we are very interested to hear from 
front-end developers how we can make WPLib Box better to help them their do their jobs.   

### Backend Developer
Here at the WPLib Box team we define a _"Backend Developer"_ as someone who focuses on the PHP, MySQL and possibly
REST API aspects of a WordPress site. In our experience backend development and plugin development go hand-in-hand
 but that doesn't mean backend developers can't have significant sway over theme code as many back end developers
 do.
 
And finally we **love** professional backend developers because frankly we are backend developers too! Without us, 
WordPress sites would never have the deep level of functionality that requires server-side coding and database 
expertise. So we are also very interested to hear from backend developers whose workflow may differ from our own
so that we can make WPLib Box better for you.   

### Project 

Most everything in WPLib Box is organized around the _"Project."_  A Project is identified by a primary local
domain name e.g. `example.local` or `example.test`.  

A Project is assigned a [directory](#base-projects-directory) for its source packages and data and media files which
will be a subdirectory of the name identified by the primary local domain contained within the 
[base projects directory](#base-projects-directory).  Thus if the base projects directory is `~/Sites` and the 
project's local domain is `example.local` then the the project subdirectory would be `~/Sites/example.local`.   

A Project also has a configuration file found in project subdirectory with the name `project.json`. It _(should)_ 
contain all the information required for WPLib Box to completely recreate a working local development environment 
for its Project.  As such, `project.json` files are typically version controlled and easily shared by team members.  

More specifically, a Project has an [Ad-hoc Stack](#ad-hoc-stack) that identifies the [Components](#component) that 
WPLib Box will run and/or make available when the project is _activated_. This ad-hoc stack is declared in the 
`project.json` file.   

### Base Projects Directory 
A directory on your [host computer](#host-machine) that is mapped to `/projects/` within WPLib Box. A typical 
example Base Projects Directory might be `~/Sites` or `C:\Sites`, if you are on MacOS/Linux or Windows, respectively.  

!!! info The projects directory inside the box will soon change
    In a near future version of WPLib Bix the `/projects` directory will be changed to `/home/box/projects`. 

### _(Software)_ Stack

In general a _"(Software) Stack"_ is ==the collection of software== used by a software application to do its job. 
 
 To host WordPress in WPLib Box the collection of software used consists of a web server like Nginx or Apache, 
 a database server like MySQL or MariaDB, a version of PHP such as 5.6 or 7.2 and possibly a cache server 
 like Memcached or Redis.
 
??? info "_Software Stack_ On Wikipedia"
    A _"[Software Stack](https://en.wikipedia.org/wiki/Solution_stack)"_ on Wikipedia &mdash; such as 
     [LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)), 
    [WIMP](https://en.wikipedia.org/wiki/WIMP_(software_bundle)), and 
    [MEAN](https://en.wikipedia.org/wiki/MEAN_(software_bundle)) &mdash; 
    is a name identifying ==sets of software needed to create a complete software solution==. 
    
    In the first of 
    these _"L.A.M.P."_ identifies _L)inux_, _A)pache_, _M)ySQL_ and _P)HP_, and LAMP is a 
    well-known stack that supports the WordPress platform.

### Stack

In the context of WPLib Box, a _"Stack"_ is ==the collection of software [components](#component)==
that turn  a basic do-anything Linux [virtual machine](#virtual-machine) into a powerhouse tailor-made 
for the local development of WordPress websites, or the development of any other web solution, for 
that matter.

Stacks can also extend other Stacks, or said another way one Stack and inherit the attributes of another. 
Our `"wordpress"` stack inherits from our `"lxmp"` stack, for example.

For WPLib Box you have both [Named Stacks](#named-stack) and [Ad-hoc Stacks](#ad-hoc-stack).

### Named Stack 

WPLib Box's _"Named Stacks"_ specifies the "[_Type_](#component-type)" of [components](#component) required 
to support a web solution such as WordPress, or any other web solution. And a Named Stack also defines the 
number of each component(s) of a given type that are required, which is typically one each.

However, a Named Stack ==is **abstract** and never used directly==; [Ad-hoc Stacks](#ad-hoc-stacks)
are used by WPLib Box instead.

The detailed specifications for the Named Stacks WPLib Box supports at any given time can be found in the 
JSON files located in `/opt/box/etc/stacks`.

!!! attention 
    The initial JSON files for specifiying Named Stacks have not yet been finalized as of version `0.17.0`.

### Ad-hoc Stack 

A WPLib Box _"Ad-hoc Stack"_ is specific to a [Project](#project), and is the collection of [components](#component) 
specified in the `"stack"` property of a a project's `project.json` file. 

Typically an Ad-hoc Stack will include all the required components for at least one named stack, such as `"wordpress"`, 
possibly its optional components, and then zero (0) of more general purposes components and/or components of 
other named stacks.  

This is an example of the default Ad-hoc Stack from the default `project.json` for `0.17.0`:

    {
        "stack" : {
            "wordpress/dbserver":	 "wplib/mysql:5.5.60",
            "wordpress/webserver":	 "wplib/nginx:1.14.0",
            "wordpress/processvm":	 "wplib/php:7.1.18",
            "wordpress/cacheserver": "wplib/redis:4.0.9",
            "wordpress/cliapp":		 "wplib/wp-cli:1.5.1",
            "mkdocs/webserver":		 "wplib/mkdocs:0.15.3",
            "box/mailsender":		 "wplib/mailhog:1.0.0",
            "box/webproxy":			 "wplib/proxy:1.14.0",
            "box/sqladmin":			 "wplib/adminer:4.6.2"
        }
    }

  
!!! attention 
    As of version `0.17.0` Ad-hoc stacks are only partially implemented, with some of the functionality
    being hard-coded into various aspects of WPLib Box. That however is planned to change in the near
    future. 

### Component Type 
 
A _"Component Type"_ is ==identified by its two-part name==, e.g. `wordpress/webserver` or `wordpress/dbserver`.  The 
first part of the name identifies the named stack and the second part identifies the 
_"[Interface](#component-type-interface)"_ within that named stack.
   
The detailed specifications for the known Component Types can be found in `/opt/box/etc/types`.

!!! attention 
    The defining JSON files for Component Types have not yet been finalized as of version `0.17.0`.  

### Component Type Interface 
 
A _"Component Type Interface"_ specifies the details neededs by WPLib Box to install and activate a component 
as part of a WPLib Box [project](#project). These details include the _"[Class](#component-class)"_ of component 
and then the details that the specific class of component requires.  

Looking specifically at Service Containers the details needed for them include port number(s), IP address(es), 
volume(s), number and usage for mount points, etc.  

The detailed specifications for the known component type interfaces can be found in JSON files 
within `/opt/box/etc/interfaces`.        

!!! attention 
    The defining JSON files for Component Types Interfaces have not yet been finalized as of version `0.17.0`.  

### Component Class 
 
A _"Component Class"_ is one of the following: 

- **Service Container**    &mdash; Services like Nginx and MySQL. 
- **Executable Container** &mdash; Executables such as the PHP CLI.
- **Script Package**       &mdash; Scripts like WP CLI, Composer and PHPUnit
- **Source Package/Files** &mdash; Source code such as WordPress core, plugins and themes
- **Data Files**           &mdash; Data like MySQL dumps, XML and JSON files. 
- **Media Files**          &mdash; Media such as images, video and PDF files.

## Suggestions for Improvement
If you have any terms to add or suggestions for improvement to our existing descriptions we **welcome** your 
suggestions.  So please help out your fellow developers and [**fork this repo**](https://github.com/wplib/box-docs), 
make your fixes and then [**submit your pull request**](https://github.com/wplib/box-docs/pulls).


[^1]: Unless you have changed your host name in the `HOSTNAME` file, which you will almost certainly have done. 