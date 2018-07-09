title: About

# About WPLib Box<br><br>![WPLib Box](https://github.com/wplib/wplib.github.io/raw/master/WPLib-Box-100x.png)

##What is WPLib Box?
In development since 2015, we have designed WPLib Box to be:
 
 
> _==The Ultimate Local Development Platform for WordPress Professionals==_ 

WPLib Box leverages both [Docker containers and a VirtualBox virtual machine](https://www.docker.com/what-container#/virtual_machines)
 to provide a best-of-breed solution that is both easy-to-use for typical WordPress use-cases but also 
 flexible enough to support practically any [software stack](/glossary#software-stack) required without 
 requiring _(almost?)_ Linux system administration skills.


## Why choose WPLib Box?

### "==It should just work=="
_"It should just work"_ has been one of our mantras from the very first day when our project lead was on a client
project hosted on WordPress VIP and it took him 4 days to get the now dead and hopefully forgotten VIP QuickStart <sic>
installed and running. 

### "==Make WordPress Easy, Make Whatever Easily Possible=="
Even though WPlib Box is designed first and formost to make local development for WordPress easy, we have 
[architected](/docs/architecture/) WPLib Box to make any [software stack](/glossary/#software-stack) you 
need to use possible.

How, you ask? [Stacks](/glossary/#Stacks) and [Components](/glossary/#components). Practically everything that runs in 
WPLib Box is part of one or more stacks, and stack is a collection of components where most components are 
_(Docker)_ [containers](/glossary/#containers), though certainly not all. 

Read about WPLib's [architecture](/docs/architecture/) to understand more.  


### ==Pre-provisioned==
Most Vagrant boxes for WordPress start with a base Linux and then build the box _"from ground up"_ ==on the 
developer's computer==, installing Nginx or Apache, PHP, MySQL, etc. This time-consuming process often takes a half hour 
or more and frequently breaks. Examples of this approach are [VVV](https://varyingvagrantvagrants.org/), 
[VCCW](http://vccw.cc/),  and [Trellis](https://roots.io/trellis/). 

However we _**pre-provision**_ WPLib Box &mdash; installing Nginx and Apache, many versions of PHP, MySQL and MariaDB, etc.
 ==before you ever download it== &mdash; so you can `vagrant up` or `vagrant reload --provision` in 
around 30 seconds _(after you first download WPLib Box, which usually takes about 5 minutes, but YMMV.)_ 

This pre-provisioning we do almost eliminates the chance of our boot-up process breaking, unlike the aforementioned 
and similar solutions.

### ==Easy XDebug==
When running WPLib Box and editing with either [PhpStorm](https://www.jetbrains.com/phpstorm/) or 
[VS Code](https://code.visualstudio.com/) _(or another IDE/editor that supports XDebug)_ you 
typically need to ==just click the _"Listen"_ button== for debugging, and then reload your page in your browser. With 
WPLib Box debugging typically _"just works."_

Compare that with other solutions that require you to configure PHP to work with XDebug. We can promise you, getting it 
to work can be [an awful lot like this](https://www.youtube.com/watch?v=k44uoVm0lPI&list=RDk44uoVm0lPI&t=32) 


### A _"==Product==,"_ not just a Project

The WPLib Team does not view our `Vagrantfile` and related provisioning scripts as our _deliverable_, ours are 
just _**examples**_ of how you can use our [Box Image](/glossary/#box-image).

Instead **we treat our Box Image as our product**, and we strive to make it bulletproof and feature-rich with 
a goal that you will be able to get the exact [web server stack](/glossary#software-stack) you need with only 
configuration &mdash; which anyone can easily do &mdash; instead of with provisioning; which requires lots of 
time and at least [junior Linux sysadmin skills](https://training.linuxfoundation.org/images/lftc_evolution_sysadmin.jpg).

??? quote "Products vs. Just Projects?"
    ==Projects== are often temporary teams whose main focus is to deliver ==on time, under budget, and within  
    scope==. And when these things are achieve, the project is considered a success. In the context of 
    a local development solution that often means a limited feature set that meets a contrained use-case, 
    and they done when they meet the needs of their developers.<br>                   
    ==Products==, on the other hand have a longer intended lifetime than a projects. They often have a clear 
    vision for what they intend to be and a consistent team design to achieve those goals. Success for products 
    is not measured in meeting milestores but instead ==on having very happy users== that use the product consistently 
    over time.  
        

### A _"==Platform==,"_ not just a Product

When we decided to expand our vision for WPLib Box we decided that what we wanted was to create a _"Platform"_ upon
which other developers with devops experience could build, and not just a product whose flavors are only vanillia 
and chocolate. 

??? quote "Platforms vs. Just Products?"
    A simple way to think about _"Platforms" vs. "Products"_ is by analogy. 
    <br><br>
    We all know that WordPress is a successful but would never have achieved the level of success ==without the hooks== 
    required to enable themes and plugins. Certainly far fewer people would have modified WordPress core to meet their 
    needs than the number who have chosen to install themes and plugins developed by others. 
    <br><br>
    So, by analogy, a _"Platform"_ is like WordPress **with** hooks compared to just a 
    _"Product"_ which is like WordPress without. Thus ==WPLib Box is like WordPress with hooks== and can easily be 
    [extended by 3rd party components](/docs/architecture/components.md).

As [described above](#make-wordpress-easy-make-whatever-easily-possible) WPLib Box wants to make any 
[software stack](/glossary/#sofware-stack) you need possible. But not only do we want to make it possible, 
==we want to make it _**easily**_ possible==, and that often means providing a simple-to-extend 
[architecture](/docs/architecture) combined with the community leadership and infrastructure needed to support 
3rd party [components](/docs/architecture/components/). And while we do not have the simple-to-extend 
architecture finalized nor the infrastructure required in-place, those are two of our highest priorities 
to pursue.

### A ==Sincere Desire== to meet your needs
Since our main goal is for WPLib Box to be the first choice of every WordPress Professional we sincerely 
want to ensure that WPLib Box meets your _specific_ workflow needs. Most alternatives to WPLib Box have a vision 
for their solution and if it aligns with your needs, great! If not, too bad; those other solutions will not deviate 
from the vision, no matter what their users would prefer.

But while we too have a vision, out vision includes meeting the needs of **all** WordPress professionals, ==so 
achieving our vision mean meeting your needs== too.  

### Full Featured, ==But Not Bloated==
Developers often fear that WPLib is, or will be _"bloated_" when we tell them we plan to meet the needs of 
*all*  WordPress professionals, but that could not be further from the truth. 

Our specific [architecture](/docs/architecture/) &mdash; a minimal [virtual machine](/glossary#virtual-machine) 
with all functionality implemented as optional [containers](/glossary#container) &mdash; ensures WPLib Box 
will be full-featured, _but never bloated._  


  

## History of WPLib Box
WPLib Box was envisioned simply after our project lead reached a breaking point of frustration with the then available 
alternatives. 

### The Impetus

Our project lead had tried to use [VVV](https://varyingvagrantvagrants.org/) on and off for months &mdash; all 
while his then-partner was effuse over VVV &mdash; yet he continued to fall back to using a local install of PHP, 
Apache and MySQL because of ==how long VVV took to provision== and ==how often it broke== leaving him with unplanned time 
required to research and solve the issue before he could actually get back to work and start developing again.

But it was not until our project lead experienced _"[VIP QuickStart](https://github.com/Automattic/vip-quickstart)" &lt;sic>_ 
that he decided to actually do something about it. He was on a client project hosted on WordPress VIP and it literally 
==took him four (4) days== to get the now dead and hopefully forgotten VIP QuickStart installed and running. 

Also, one of our project lead's motivations was to be able to provide a local development experience 
[_"that just worked"_](#it-should-just-work) for newbie WordPress developer who attended the WordPress Developer Meetup 
he was running at the time. He had tried VVV but typically ==spent most of the two (2) hour sessions== just getting it 
VVV to work on workshop attendee's computers. Clearly this was not viable!

Then our project lead researched alternatives and found [ScotchBox](https://box.scotch.io/) which billed itself as a 
dead-simple LAMP stack for local development.  And it was dead simple; and it was pre-provisioned _([like WPLib Box is now](#it-is-pre-provisioned))._
It was perfect! I could use it for both developing client projects and and for workshops at the WordPress Developer Meetup!

Except. ==ScotchBox lacked/lacks XDebug==. Which made it not perfect for a WordPress Developer Meetup workshops because 
==getting XDebug working can be a major PITA==.  Worse, [even though](https://github.com/scotch-io/scotch-box/issues/7) 
[many people](https://github.com/scotch-io/scotch-box/issues/90) 
[were clamoring](https://github.com/scotch-io/scotch-box/issues/203) 
[for it](https://github.com/scotch-io/scotch-box/issues/244), 
the developer of ScotchBox [said no](https://github.com/scotch-io/scotch-box/issues/7#issuecomment-169764612) to adding
XDebug as a standard feature.  

So this third roadblack was the last straw. We decided the only way to get ==the power and control== that we needed, and 
frankly that ==all developers need==, was to architect and build it ourselves!  

### The First Generation

The goals for the first generation of WPLib Box _(Nov 2015 through Feb 2017)_ was ==to create a stable LEMP box that 
made using XDebug easy== and was as easy to implement as possible and that ideally _"just worked."_  We built it in 
iterations by focusing on _"the next simplest thing we can add"_ which allowed us to deliver on our vision fairly 
quickly. 

The final release of this generation was [`0.11.2`](https://github.com/wplib/wplib-box/releases/tag/0.11.2).

### The Second Generation

The goal for the 2nd generation was to make WPLib Box ==far more flexible== by replacing the internal services ==with 
Docker containers== thus allowing easy mix-and-match of services.  

Unfortunately, that was easier said than done.  As such versions `0.12.0`, `0.12.1`, `0.13.0`, `0.14.0`, and `0.15.0` 
were effectively unusable and our offerings during 2017 were abysmal. It was not until we brought on a new team member 
&mdash; an incredibly skilled Linux sysadmin &mdash; that we were able to get out of these doldrums 

Following that bleak period we released a usable `0.16.0` in May 2018 quickly followed by `0.16.1`, `0.16.2` and very
recently in early July 2018 we released `0.17.0` which is &mdash; by far &mdash; our most usable and workable release 
ever.  

What's more we plan a simple bug fix `0.17.1` **and** a specialty release to support the 
[WordPress Meta Environment](https://github.com/WordPress/meta-environment), hopefully before the first of August 2018.   

### The Third Generation

Which brings us to our _(near)_ future plans; our third generation. At a high level our 3rd generation 
WPLib Box will: 

1. Free itself from the shackles of Vagrant,  
2. Have an installer each for Mac and for Windows, and 
3. Support multiple projects[^1] in a single install of WPLib Box.

Beyond that you should checkout out our [roadmap](/roadmap) where we go into a lot more details.

[^1]: We chose to call future WPLib Box _"Multi-project"_ instead of _"Multisite"_ to avoid confusion with 
[WordPress Multisite](https://www.wpbeginner.com/glossary/multisite/). Thus each WordPress install is a _"project,"_ 
and WPLib Box can support both WordPress Single-site and WordPress Multisite installations.
 
