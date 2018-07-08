title: GitHub 

#Github Repos for WPLib Box

The following are the GitHub repositories that collectively contribute to the software platform that is WPLib Box at the time[^1] of this writing. 

## Primary Repositories

### [wplib/wplib-box](https://github.com/wplib/wplib-box)
This is the main repository for WPLib Box from which [the releases](https://github.com/wplib/wplib-box/releases) 
are [generated](https://github.com/wplib/wplib-box) and [the issues and feature requests](https://github.com/wplib/wplib-box/issues) 
are tracked.
  
### [wplib/box-support](https://github.com/wplib/box-support)
Contains the [**WPLib Box Support plugin**](https://github.com/wplib/box-support) that provides, among other things, 
password-free login[^2] to the WordPress admin. 
  
### [wplib/box-welcome](https://github.com/wplib/box-welcome)
Contains the [**WPLib Box Welcome theme**](https://github.com/wplib/box-welcome) which is an entry point for 
new users of WPLib Box. 

In future versions it will be replaced by a desktop admin console for configuring the box.
  
### [wplib/box-scripts](https://github.com/wplib/box-scripts)
Contains the Bash-based command line tool for managing WPLib Box after running `vagrant ssh` to enter into the 
Linux-based of WPLib Box. 

In future versions this will be replaced with a [Go-based command line utility](#wplibbox-cli).
  
### [wplib/box-docs](https://github.com/wplib/box-docs)
Contains the Markdown source for this MkDocs-generated set of documentation.
 
### [wplib/box-installer](https://github.com/wplib/box-installer)
In the near future &mdash; once we convert WPlib Box to a fully multi-project box &mdash; this repository will contain 
`.exe` and `.pkg` installers for Windows and Mac, respectively.  

### [wplib/box-cli](https://github.com/wplib/box-cli)
In the near future this repository will contain Go source code for the future command line utility for 
managing WPLib Box.  

### [wplib/box-api](https://github.com/wplib/box-api)
In the near future this repository will contain Go source code for the REST API that will allow WPLib Box 
to be fully automated using RESTful API calls.  

### [wplib/box-admin](https://github.com/wplib/box-admin)
In the near future this repository will contain the source code for an Electron-based desktop app that will allow 
non-technical end-users to manage and configure WPLib Box.  

### [wplib/website](https://github.com/wplib/website)
Contains this source code for our primary website [wplib.org](http://wplib.org), but not for [wplib.org/box/](http://wplib.org/box/) 
which is contained in the [wplib/box-docs](#wplibbox-docs) repository.  

### [wplib/logos](https://github.com/wplib/logos)
The offical logos for WPLib Box.

## Docker Containers Repos

### Box-global Components
#### Service Containers
##### [wplib/proxy-docker](https://github.com/wplib/proxy-docker)
##### [wplib/maihog-docker](https://github.com/wplib/maihog-docker)
##### [wplib/adminer-docker](https://github.com/wplib/adminer-docker)

### Project-specific Components
#### Service Containers
##### [wplib/php-docker](https://github.com/wplib/php-docker)
##### [wplib/nginx-docker](https://github.com/wplib/mkdocs-docker)
##### [wplib/apache-docker](https://github.com/wplib/apache-docker)
##### [wplib/mysql-docker](https://github.com/wplib/mysql-docker)
##### [wplib/mariadb-docker](https://github.com/wplib/mariadb-docker)
##### [wplib/redis-docker](https://github.com/wplib/redis-docker)
##### [wplib/memcached-docker](https://github.com/wplib/memcached-docker)

##### [wplib/mkdocs-docker](https://github.com/wplib/mkdocs-docker)

#### Executable Containers
##### [wplib/php-docker](https://github.com/wplib/php-docker)
##### [wplib/composer-docker](https://github.com/wplib/composer-docker)
##### [wplib/wp-cli-docker](https://github.com/wplib/wp-cli-docker)
##### [wplib/wordpress-docker](https://github.com/wplib/wordpress-docker)

### Potential Containers 
##### [wplib/caddy-docker](https://github.com/wplib/caddy-docker)
##### [wplib/dns-docker](https://github.com/wplib/dns-docker)

### Deprecated Repositories
##### [wplib/php-fpm-docker](https://github.com/wplib/php-fpm-docker)
##### [wplib/apache2-docker](https://github.com/wplib/apache2-docker)
##### [wplib/caddy-package](https://github.com/wplib/caddy-package)
##### [wplib/box-cli2](https://github.com/wplib/box-cli2)
##### [wplib/ERROR-CODES](https://github.com/wplib/ERROR-CODES)







[^1]: Last updated 2018-07-07.
[^2]: Password-free login **only works** when running locally within WPLib Box, unless otherwise configured by hooks.