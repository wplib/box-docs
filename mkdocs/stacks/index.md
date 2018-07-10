title: Stacks

# [Stacks](/glossary#stack) in WPLib Box 

In WPLib Box, our _"Stacks"_  drive practically all functionality. 

Our Stack is a collection of versioned [Components](/components/) that collectively implement WPLib Box's 
functionality. It is this stack and these components that provides the ==power and flexibility no other 
contemporary local development solution can match==. 

## WPLib Box defines abstract [Named Stacks](#/glossary#named-stack)
In WPLib Box the default "_Named Stack"_ is the `"wordpress"` stack. 

!!! info "No surprise there. You were expecting something else?"

The WordPress stack defines the [types of components](/glossary/#component-type) included in the stack. 

## [Projects](/glossary#project) get an [Ad-hoc Stack](/glossary#ad-hoc-stack)
Each _"Project"_ gets an _"Ad-hoc Stack"_ comprised of the _"[Component Types](/glossary/#component-type)"_ needed 
by the project. 

The list of components is derived from at least one [Named Stack](#/glossary#named-stack) &mdash; like `"wordpress"` 
&mdash; and should include all the required components, any optional components and potentially some general purpose 
components.  

The Ad-hoc Stack can also include components from more than one Named Stack, assuming the components are not mutually 
exclusive.
 
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