title: WP CLI

# Using WP CLI with WPLib Box

While you certainly _can_ install WP CLI on your [host computer](/glossary/#host-machine) and use it with your 
WPLib Box project, hopefully you won't have to as  we've ==implemented WP CLI within of WPLib Box==.

!!! bug 
    Unfortunately [WP CLI is broken in `0.17.0`](https://github.com/wplib/wplib-box/issues/477) due to our changing the 
    project path in the VM but not changing in the WP CLI container. ==This should be 
    [fixed soon in `0.17.1`](https://github.com/wplib/wplib-box/milestone/33)==.

## Using WP-CLI
[WP-CLI](http://wp-cli.org/) is installed in the WPLib Box virtual machine so to use it you first 
[SSH into WPLib Box](/docs/tutorials/secure-shell) and then run your WP CLI command, for example:

    vagrant ssh
    wp plugin list

## Implementation
Our implementation of WP CLI follows WPLib Box's [philosophy of containerization](/philosophy/#functionality-should-be-containerized) 
and is thus implemented with our [own Docker container](https://hub.docker.com/r/wplib/wp-cli/).  

Our `wp` command is itself is a Bash script which is designed to invoke the WP CLI container and that script 
can be found at `/opt/box/bin/wp` after you `vagrant ssh` into WPLib Box.  
 
 
## Current Limitations

- ==The `wp package` subcommand is currently not supported.== &mdash; This is due to the fact our WP CLI is packaged in 
a Docker container and currently our container does not support a method to add packages to the inside of a container.
We do [have plans to correct this](https://github.com/wplib/wplib-box/issues/483), however.       

- Other commands may also have issues. If you find this to be the case ==please [contact our support](/support/)== 
to let us know so we can address sooner than later.
