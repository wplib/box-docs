title: Troubleshooting

# Troubleshooting WPLib Box

## Please [Report the Issue](https://github.com/wplib/wplib-box/issues/new) on GitHub

??? info "Even if you do find a solution, please report the issue..." 
    Even if you do find a solution please [**report the issue**](https://github.com/wplib/wplib-box/issues/new) 
    so we can either fix it or document it to make using WPLib Box easier for everyone.   

		
## If your browser times out

??? info "This in our **most common** issue"
    If you have WPLib Box **installed more than once** for the same local domain
    name it will unfortunately not load. And as long as we are still 
    using Vagrant this will continue to be a problem. Fortunately, we will be 
    off Vagrant soon enough.<br><br>
    If your browser times-out trying to load [**wplib.box**](http://wplib.box) check 
    [**your hosts file**](https://support.rackspace.com/how-to/modify-your-hosts-file/) 
    to see if you have more than one IP address entry mapped to the `wplib.box` domain 
    and its various subdomains.

## Trouble with VirtualBox

??? info "If you have problems installing or running VirtualBox"  
    First, try Googling the error messages you get when trying to install. VirtualBox is 
    independent of WPLib Box and thus you will often find solutions online. 

## Problems with Vagrant 

??? info "If Vagrant is giving you trouble"  
    Try running `vagrant up --debug` to see if it can reveal any issues with your system that you are able to correct.  You may want to redirect to a debug log so you can read the output in your text editor:
       
        vagrant up --debug > vagrant.log 2>&1

    If you can't find the solution to your problem using the `--debug` switch 
    please provide your `vagrant.log` via Slack or GitHub or email at 
    [team@wplib.org](mailto:team@wplib.org) when requesting help.

## Nothing Here Solved Your Problem
 
??? info "If you did not find your answer in any of the items listed" 
    If you do not find a solution, [join our Slack](https://launchpass.com/wplib) to get help
    from our team in the `#box` channel.<br><br>Don't be shy, **we really do 
    want to hear from you**  as it will help us make your experience with 
    WPLib Box and everyone else's much better.<br><br> 
    If your problem is Vagrant-related &mdash; as most WPLib Box problems 
    unfortunately often are &mdash; please provide your `vagrant.log` **as 
    described above in [_vagrant up_ is failing](#vagrant-up-is-failing)**. 
    _(We will be so happy once we have eliminated the need for Vagrant. Soon!)_

