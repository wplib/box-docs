title: FAQ

# OLDER CONTENT; NOT YET EDITED

## How do I Deploy My Site from WPLib Box?
Deployment to a production or staging server is extremely simple. Just:

1. Copy the entire contents of the `www/` directory to the website root of the server where you are hosting your site.
2. Using a SQL client tool such as [Sequel Pro](http://www.sequelpro.com/) or [Navicat](https://www.navicat.com) export aka _"dump"_ your database to a `.sql` file.
3. Import your `.sql` file into your web host's [MySQL](https://www.mysql.com/) or [MariaDB](https://mariadb.com) server which may be referred to as _"executing"_ your SQL file.
4. Modify `www/wp-config-local.php` on your web host to use your web host's database credentials and any other configuration options that differ on your production or staging server.
5. In future deployments be sure not to overwrite your web host specific `www/wp-config-local.php` file.

And except for the following NOTE, that is it.

**NOTE:** You will need to run whatever process you normally run to change the URLs from your local URLs to your production or staging URLs. 
There are many solutions to this although not one ideal solution thus explaining how to do this is out of the scope of this FAQ. But 
[let us google it for you](https://www.google.com/#q=changing%20urls%20when%20moving%20wordpress%20site%20-codex).

## How do I Use WPLib Box on New Projects? 
To use WPLib Box on new projects just copy the `Vagrantfile` and the `scripts/` directory from this repository to your new project and [change 
the domain name](https://github.com/wplib/wplib-box#setting-the-domain-name) to the local domain name for your project.  The only _”constraint” (that we are currently aware of)_ is you will need to have 
your website root in a `www/` directory that is a sibling to `Vagrantfile` and to `scripts/` but otherwise it should all just work using `vagrant up`.

**NOTE:**: You do not have to organize the WordPress directory structures like we have with `/www/content` and `/www/wp`; you can easily use the 
standard directory layout used by WordPress core e.g. `www/wp-content/` and `www/`, respectively.

## How do I Use WPLib Box on Pre-Existing Projects?
To use for an existing project, you follow the same instructions as for new projects; copy the `Vagrantfile` and the `scripts/` directory from 
this repository to your new project, [change the domain name](https://github.com/wplib/wplib-box#setting-the-domain-name) to the local domain name for your project and move your website root into a `www/` 
directory that is a sibling to `Vagrantfile` and to `scripts/` and then `vagrant up`.

If you cannot put your code into a `www/` subdirectory for some reason you can put the `Vagrantfile` in your web root and change the line that 
starts with `config.vm.synced_folder` to be:
 
     config.vm.synced_folder ".", "/var/www" 

If you cannot create a `scripts/` directory in the same directory as your `Vagrantfile` you can name that directory something else &mdash; such as 
`wplib-scripts/` &mdash; and then search for `scripts/` in your `Vagrantfile` and replace it with whatever you named your directory, e.g. 
with `wplib-scripts/` as in our example.

## How do I Configure Composer to Work with WPLib Box?
Configure `composer.json` however you like; WPLib Box is agnostic with respect to Composer. 

Yes, we do include a `composer.json` with our WPLib Box repository but only so that WPLib Box will just work, **out-of-the-box** _(yeah, sorry for the pun!)_

## How do I Import a MySQL Database?
When the box is created, a default WordPress database is installed. If you need to import a different dataset or restore a backup of the data, you can simply `vagrant ssh` into the guest and perform a MySQL import.

To do this, first copy your MySQL database dump to a `/sql` sub directory in your project directory _(your `Vagrantfile` is in your project directory.)_  Assuming you called your database dump `my-db.sql` then run the following commands in your host computer's command line/terminal window when in your project directory:

    cd /your/project/directory
    vagrant ssh
    box import-db my-db.sql
Be sure to [backup your database](#backup-db) **BEFORE** you run the `import-db` command.
    
## How do I backup the MySQL database in the box?
If you have a live database inside of WPLib Box you may want to backup the database to the `/sql/` directory in your project root.  You can do that like so:

    cd /your/project/directory
    vagrant ssh
    box backup-db
    
The above commands will backup your database to `/your/project/directory/sql/current.sql`.  If there already was a `current.sql` it will be renmed to `previous1.sql` and `1` will be incremented each time there is a new backup.
    
## Which PHP Versions are Available?
Currently, the box has PHP `5.6`, PHP `7.0` and PHP `7.1`, with PHP `7.0` running by default. Versions `5.6` and `7.0` are each implemented using their own Docker container and the latter is installed directly into Ubunutu in our box. All modules installed are configured for both versions of PHP.

## How do I Switch PHP Versions?
The PHP version in use by the site is set in the `project.json` file in the `services` section and the `processvm` property. This will set both the web version and the command line version. 

To change both web and command line versions to PHP `7.1`, SSH into the running Vagrant box from your project directory and then run the `box php7.1` command:

    cd /your/project/directory
    vagrant ssh
    box php7.1

To change to `7.0` or `5.6`, use the same command but replace `7.1` with `7.0` or `5.6` from while SSHed into the box, e.g.:

    box php7.0
or

    box php5.6

## How do I Install PhpMyAdmin?
We decided not to include phpMyAdmin in the core box image because it installs files for Apache that we don't need so we decided to make it optional. 

To install phpMyAdmin look for the instructions [**here**](https://github.com/wplib/wplib-box/issues/117#issuecomment-230113032).

## How do I Get a URL to Provide Access to My Box's Site From the Internet?

The WPLib Box image has [localtunnel.me](https://localtunnel.me) pre-installed in the box. Simply run these commands from your host's command line:

    vagrant ssh
    lt --port 80
    
This will provide you with a URL to share the local site until you exit the command by either terminating the program or shutting down the machine.

You can also use [Vagrant Share](https://www.vagrantup.com/docs/share).

## How do I debug with Visual Studio Code?

The configuration file for Visual Studio Code is already included in the respository. Ensure that you have installed the [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) extension for Visual Studio Code.

## How do I access Adminer?

[Adminer](https://www.adminer.org/) is a web front end to administer the MySQL server. End users can access Adminer at http://adminer.{your-domain}. If you have not changed the box domain name, that would be [http://adminer.wplib.box](http://adminer.wplib.box).

The credentials are:

+ Host: 172.17.0.1
+ Username: wordpress
+ Password: wordpress
+ database: wordpress


## How do I access MailHog?

[MailHog](https://github.com/mailhog/MailHog) is an email testing tool for development purposes. In WPLib Box, all outgoing emails are captured and available for inspection via the MailHog interface: [http://mailhog.wplib.box](http://mailhog.wplib.box). If you have changed the box domain, you can use http://mailhog.{your-domain}.

## How do I fix the Vagrant 1.8.6 Bug?

Vagrant `1.8.6` appears to have an issue with auto-configuring its network. Until this is fixed by Vagrant there is a workaround which requires you to SSH into the box after `vagrant up`. It is not difficult &mdash; the instructions appear longer than the task itself &mdash; just follow these steps:

1. Once your box is running _(after a `vagrant up`)_ run `vagrant ssh`.
2. Once _"inside"_ WPLib Box type `sudo nano /etc/network/interfaces` to load the network config into the Nano editor.
3. Look for the second _(2nd)_ occurence of `auth eth0` and change it to `auth eth1`.

4. Also change the `eth0` in the next line _(`iface eth0 inet static`)_ to be `eth1`. The result should be `iface eth1 inet static`.
5. Delete both lines that begin with `#VAGRANT-` by moving your cursor to those lines and pressing `Ctrl-K` once for each line.
6. Save the file by pressing `Ctrl-O` then pressing `[Enter]`.

7. Exit the editor with `Ctrl-X`.
8. Exit _"inside"_ WPLib Box _(the SSH session)_ by typing the `exit` command.

If you somehow mess up while editing you can exit Nano and start over by pressing `Ctrl-X` then pressing `N` _(for "No")_ when it asks you if you want to _"Save the buffer?"_.

In addition you need to make a simple change to `Vagrantfile` using whatever editor you normally use to edit code. Find the following line in `Vagrantfile` around line `264`:

    config.vm.network 'private_network', ip: IO.read('IP').strip

And add `, auto_config: false` to the end, like so:

    config.vm.network 'private_network', ip: IO.read('IP').strip, auto_config: false

Then run `vagrant reload`.  This should fix it.  

Also you should not need to revert that after upgrading to a new version of Vagrant **_unless_** you need to [change the box's IP address](#change-ip).

## How do I switch from Nginx to Apache (or vice versa)?
By default, WPLib Box uses Nginx as its webserver. However, Apache is available and can be switched out with Nginx.
The box CLI has a command, `set-web-server` to accomplish this.

For example, to switch from Nginx to Apache:
 
+ Log in to the box using `vagrant ssh` on your host machine.
+ Enter the following command: `box apache` to make Apache the running webserver.
+ Conversely, you can `box nginx` to switch from Apache to Nginx.

## How do I switch from MySQL to MariaDB (or vice versa)?
The box runs MySQL as the default database, however MariaDB is available. To configure the box to use
MariaDB instead, use the `box` command _(which will dump the contents of
the current database and import into the new database)_:

+ Log in to the box using `vagrant ssh` on your host machine.
+ Enter the following command: `box mariadb` to use MariaDB.
+ Conversely, you can `box mysql` to switch from MariaDB to MySQL.

## How do I see the logs for Docker container Foo?
The logs for a Docker container can be viewed using the command `docker logs foo`, where `foo` is the name of the
container whose logs you wish to view.

To get a list of containers you can run the following command:

    docker container ls

To see just the names run this command:

    docker container ls --format '{{.Names}}'

At the time of this writing the container names in WPLib Box were _(though not all run all the time):_

- `mailhog`
- `mariadb`
- `mysql`
- `memcached`
- `redis`
- `php5_fpm`
- `php7_fpm`
- `apache`
- `nginx`
- `proxy`

In the case of the webserver containers, these logs contain both the access and error log entries.

## If you get 404 Not Found on Vagrant Up
If you get a 404 error from `vagrant up` chances are you are on a `1.x` version of Vagrant and need to upgrade to a `2.x` version.  The `1.x` version does not recognize the new Vagrant Cloud and still looks to [atlas.hashicorp.com](https://atlas.hashicorp.com) for our Vagrant image, which is obviously no longer there _(not sure why Hashicorp does not support redirects here, but maybe Vagrant `1.x` deoes not follow them?)_ 

Upgrading Vagrant to `2.x` then running `vagrant plugin repair` should resolve this issue. 

Here is what this error looks like on the command line:

```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'wplib/wplib' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: 0.16.0
The box 'wplib/wplib' could not be found or
could not be accessed in the remote catalog. If this is a private
box on HashiCorp's Atlas, please verify you're logged in via
`vagrant login`. Also, please double-check the name. The expanded
URL and error message are shown below:

URL: ["https://atlas.hashicorp.com/wplib/wplib"]
Error: The requested URL returned error: 404 Not Found
```




## Development Approach 
_(These principles apply to our process prior to when we reach version 1.0.)_
## Frequent Releases
Our development approach is to create frequent `0.x` releases as we work towards version `1.0`. Currently we plan a new release approximately once every three (3) weeks, although the distance between some releases may take longer as our client obligations override our ability to stay on deadline.

## The Smallest Next Thing
For each of these releases we ask ourselves what is the _smallest thing_ we can do that will have a meaningful positive impact on either our existing users or new prospective users. And then we [schedule it as a milestone](https://github.com/wplib/wplib-box/milestones) and start working.  

## Flexible Priorities
Currently it is hard for us to look past the next milestone in specifics, as we are very aware of and interested in feedback from users; we'd rather be able to react to feedback when possible than put it off until after a really long time later.

## Move Fast, Resolve Issues Quickly
Also, given WPLIb Box is `pre-1.0` and we are moving fast, we may break things and/or implement a new feature where we have not thought through all the use-cases, but we'll move quickly to resolve any issues our fast moving creates and hopefully offer workarounds [via Slack](https://slackpass.io/wplib) or GitHub issues in the mean time. For example, we recently implemented Nginx as a Docker container but did not provide user access to update the Nginx config files _(but we plan to correct that the next release.)_  

## Until Version 1.0
However, as we get closer and closer to `1.0` we'll be breaking things less and less and we'll be implemented fewer new features that are not fully baked upon release.  It's basically our agile process of working towards a `1.0` release.


## Business
## What is our Business Model?
We are a consulting company that is transitioning to a product company that offers products and services
for improving Developer Experience for PHP developers who have chosen to use WordPress as a platform. 

If you have idea ahout how we could help your development organization with workflow please [**contact
us**][1] with your ideas and we'll see if we can help. 




 [1]: mailto:team@wplib.org
