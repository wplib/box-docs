title: Philosophy

# Philosophy Governing WPLib Box

The following philosophies are those the WPLib Box team uses to govern our strategic vision and tactical decision 
regarding everything we do related to WPLib Box.  

## Make development easier   

Our #1 job is to ==make WordPress development easier==. Full stop.

Everything we decide and everything we do contributes to this goal.  Both for the site, theme and/or plugin 
building newbie as well as the most advanced WordPress developer on the planet.

## It should just work 

First and foremost, WPLib Box should be like dial tone on a telephone land line and that is it 
==should always just work==.  

If at all possible WPLib Box should never leave you stuck with a broken local development environment simply 
because you may do not have the Linux expertise or the time to fix a problem, especially when you are in the 
11th hour of an intense project that needs to be done tomorrow morning! 

The box ==should never fail== on you in those, or any circumstances.   

!!! info "Yes _"never failing"_ is idealistic" 
    <p>Yes, we admit, _"never failing"_ is idealistic.</p> 
    <p>However, we can and do ==strive to achive as close to 100% of that goal== as we possibly can. It was for 
    this reason we decided to eliminate the need for Vagrant _(which we should get to in the very near future.)_</p> 
    <p>So **our primary goal** is: _You should always be able to depend on WPLib Box._</p>
    <p>But because software is complex and we cannot _guarantee_ that the software we depend on 
    will not leave you stuck, we are more than happy to [support you](/support/) for free whenever you need, 
    especially on Slack.</p>   


## Provide instruction in error messages  

If WPLib Box generates an error message, the message ==should include the instructions== that **you** would need 
to resolve the issue.  

This is an ideal, but the only acceptable exception to this ideal is if that it is simply not possible.

## Functionality ==should be in the box== 

If functionality that can benefit users _**can**_ be installed and run in the box, it _**should**_ be installed and 
run in the box _(instead of needing to be installed and run on the [host computer](/glossary#host-machine).)_

This means that you should not need to install Grunt/Gulp/WebPack, Composer, WP CLI, PHPUnit, etc. on your host 
 computer when you have WPLib Box to do it for you. Everything you want or need for WordPress development should be
  pre-packaged and available  to run from within the box.    

Why? So you never need to try to install and then have to debug the install of a new developer tool again. 
Thus, ==if can run in the box, it should run in the box.==

!!! info "We are not here yet"
    While this is one of the things we badly want to see happen, we have not gotten all the the standard functionality
    WordPress developers will want to use running in the box.<br><br> 
    For example, we do have Composer and WP CLI, but not PHPUnit or anything requiring NodeJS/NPM. Why? Because unlike 
    servers delivered as binaries, all of these tools are delivered as scripts that require a PHP or Javascript 
    runtime. And while we _could_ package the runtime with their script into a container we want to implement a better 
    architecture that allow us to pair scripts with a container that provides the necessary runtime.<br><br>
    Still, we know that [shipping is a feature](https://a16z.com/2014/04/16/shipping-is-a-feature-some-guiding-principals-for-people-that-build-things/) 
    so if you have an urgent need for any of these tools or other tools that are not currently implement please reach
    out to us on Slack 
    

## Functionality should be containerized 

If we or any users add functionality to WPLib Box it _**should**_ be added via container, never installed directly 
in the [virtual machine](/glossary/#virtual-Machine) unless otherwise impossible.

All service running in the box, and all executables to be run in the box should be packages in a container. We will 
never just install software directly into Linux &mdash; except Docker itself and a few other infrastructure bits &mdash; 
and we'd advise you not to do so either.

This means at times software will not behave as expected because the software was written within expecting to be 
run in a container. If you run into any of these cases we ask that you [contact us for support](/support/) so we 
can either find a solution for you or a workaround. 


## Proactively notify about issues 

If WPLib Box can in any way proactively recognize that a user would be having an error then it should notify the 
user of that error in advance, in an non-obtrusive and easily dismissable manner.

!!! info "We are not there yet"
    While this is one of the things we badly want to see happen, we have not gotten to the point where we 
    can users of issues in advance the way we envision. But good things come to those wait _(just a bit longer.)_  

## Empower best-practices   

Too many people avoid best practices in WordPress because following them can take too much time to setup and learn. 

So a key goal for WPLib Box is to ==make following best practices easier than not==. 

Be it 1.) using test, stage and production servers, 2.) implementing automated testing, 
3.) version-controlling your source, or 4.) developing structured object-oriented code 
WPLib Box should make implementation of those best practices and more trivial,  
and it should make learning how to use them easy. <br><br>
So much so that you'll wonder how you ever managed to 
[cowboy code](https://brudtkuhl.com/cowboy-coding-to-professional-developer-wckc-2015/) in your past.

!!! info "We are not here yet"
    While this is one of the things we badly want to see happen, we have not gotten to the point where we 
    can empower best practices in the way we envision. But good things come to those wait _(just a bit longer.)_  


## These are not all

This page is not yet complete, so expect more points related to our philosophy in the future. 
