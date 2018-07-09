title: Composer

# Using Composer with WPLib Box

While you certainly _can_ install Composer on your [host computer](/glossary/#host-machine) and use it with your 
WPLib Box project, hopefully you won't have to as  we've ==implemented Composer within of WPLib Box==.

!!! bug 
    Unfortunately [Composer is broken in `0.17.0`](https://github.com/wplib/wplib-box/issues/473) due to our changing 
    the default username for WPLib Box but not changing in the Composer container. ==This should be 
    [fixed soon in `0.17.1`](https://github.com/wplib/wplib-box/milestone/33)==.

## Using WP-CLI
[WP-CLI](http://wp-cli.org/) is installed in the WPLib Box virtual machine so to use it you first 
[SSH into WPLib Box](/docs/tutorials/secure-shell) and then run your Composer command, for example:

    vagrant ssh
    composer install

## Implementation
Our implementation of Composer follows WPLib Box's [philosophy of containerization](/philosophy/#functionality-should-be-containerized) 
and is thus implemented with our [own Docker container](https://hub.docker.com/r/wplib/composer/).  

Our `composer` command is itself is a Bash script which is designed to invoke the Composer container and that script 
can be found at `/opt/box/bin/composer` after you `vagrant ssh` into WPLib Box.  
 
 
## Current Limitations

- Some commands may have issues. If you find this to be the case ==please [contact our support](/support/)== 
to let us know so we can address sooner than later.
