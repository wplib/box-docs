title: Stacks

# [Stacks](/glossary#stack) in WPLib Box 

_"Stacks"_  empower practically all functionality found in In WPLib Box. 

A WPLib Box stack is a collection of versioned [Components](/components/) that together implement WPLib Box's 
functionality. It is these Stacks and these Components that provide unmatched power and flexibility. 


## Named Stacks

In WPLib Box there is the concept of _"[Named Stack](/glossary#named-stack)"_. A Named Stack specifies a list of 
[Components Types](/glossary/#component-type) that are either required or optional 
to support the software the stack is designed for. 

And, no surprise, the default Named Stack for WPLib Box is the `"wordpress"` stack. 

!!! info "You were expecting something else?"

If you are familiar with object-oriented programming in PHP a Named Stack is like a _"class"_ and the Project Stacks 
described next are similar to _"instances"_ of that class.  

## Project Stacks
Each _"[Project](projects/)"_ gets a _"[Project Stack](/glossary#project-stack)"_ comprised of the 
[Component Types](/glossary/#component-type) needed by the project. 

The list of components is derived from at least one [Named Stack](#/glossary#named-stack) &mdash; like `"wordpress"` 
&mdash; and should include all the Named Stack's required components, any of its optional components 
and potentially some general purpose components. The Project Stack can also include components from other Named Stacks, 
assuming the components are not mutually exclusive.
 
## The _"WordPress"_ Stack   

The WordPress stack is comprised of the following component types:

Component Type            | Required | Examples              
--------------------------|----------|----------------------- 
`"wordpress/webserver"`	  |  Yes     | Apache or Nginx       
`"wordpress/dbserver"`	  |  Yes     | MySQL or MariaDB      
`"wordpress/processvm"`	  |  Yes     | PHP                   
`"wordpress/core"`        |  Yes     | WordPress core source 
`"wordpress/cacheserver"` |  No      | Memcached or Redis    
`"wordpress/cliapp"`      |  No      | WP CLI    

### The _"WordPress"_ Stack in `project.json` form:   
                                     
The following is how `0.17.0` currently implements the WordPress stack 

    {
        "stack" : {
            "wordpress/dbserver":	 "wplib/mysql:5.5.60",
            "wordpress/webserver":	 "wplib/nginx:1.14.0",
            "wordpress/processvm":	 "wplib/php:7.1.18",
            "wordpress/cacheserver": "wplib/redis:4.0.9",
            "wordpress/cliapp":		 "wplib/wp-cli:1.5.1"
        }
    }

!!! note "Theory and practice do not yet align in `0.17.0`"
    Savvy readers will note that `"wordpress/core"` has yet to be implemented via the `project.json` 
    loader as of `0.17.0`. That, of course, is coming soon.    

## The _"LxMP"_ Stack   

In addition to the WordPress stack WPLib Box has the more generic LxMP stack, which is basically 
what is well-known as the LAMP/LEMP stack.
   
The LxMP stack is comprised of the following component types:

Component Type        | Required | Examples              
----------------------|----------|----------------------- 
`"lxmp/webserver"`	  |  Yes     | Apache or Nginx       
`"lxmp/dbserver"`	  |  Yes     | MySQL or MariaDB      
`"lxmp/processvm"`	  |  Yes     | PHP                   
 
    
WPLib Box's ==WordPress stack actually inherits from and extends== the LxMP stack.

## Build-Your-Own Stack!   

While we are definitely targeted WordPress professionals we deliberately chose to 
architect the core of WPLib Box was to be completely neutral with respect to web CMS 
and/or web framework. Everything about the vision for WPLib Box is that its 
support for WordPress is implemented using features that anyone else can use to 
add support for another CMS or another framework.  

So, if you are a champion for another CMS or another web framework and would like
us to teach you how to build the components needed to support your favorite web 
solution, please [reach out to us via our Slack](/support#slack).