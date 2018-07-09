

## Why is WPLib Box Caching Things?
WPLib Box installs Redis for persistent object caching. To disable this simply rename `www/content/object-cache.php` to something like `object-cache.disabled.php`.  But we do [**have plans**](#plans) to add numerous ways to do this.
 
If you need to clear the cache the easiest way at the moment is to run `vagrant reload` from your development (host) computer.  

## How do I Flush the Redis Persistent Object Cache?
If you need to test with the persistent object cache, but you are running into the need to flush a corrupted cache you can simply run the following command from your host's command line:

    vagrant ssh
    redis-cli
    flushall
    exit

## Why is the Directory Layout used Not _"Standard?"_

By default WPLib Box uses the [WordPress Skeleton](https://markjaquith.wordpress.com/2012/05/26/wordpress-skeleton/) layout published by Mark Jaquith in 2011. We chose it because unlike the standard WordPress directory layout it is [Composer](https://getcomposer.org/)-friendly which is almost a requirement these days for professional-level  PHP development. 

But if you are not yet using Composer or don't feel you have the need for it you can you the _"Standard"_ WordPress directory layout instead. See the three (3) simple approaches that follow in the next FAQ.

## Can I use the Standard WordPress Directory Layout?

Absolutely. 

To be clear we assume you mean the directory layout that has the following subdirectories:

    /wp-admin/
    /wp-content/
    /wp-includes/
    
_(Those directories are the exact layout you'll see in a download of WordPress from WordPress.org.)_

#### The Manual Approach
To use the Standard WordPress directory layout open up Mac Finder or Windows Explorer and navigate to your project's `/www` directory _(the project directory is the one containing `Vagrantfile` and the `/scripts` folder.)_ Then do the following:

1. Delete the `/www/wp/wp-content` directory; you don't need it. _(Uh, after checking you did not store anything in `/www/wp/wp-content` by accident. If you did, move it out then delete the directorty.)_

2. Move all the remaining files and directories up one level in the directort hierarchy; from `/www/wp` to `/www`.

3. Rename `/www/content` to `/www/wp-content`

4. Delete `/www/wp`

5. In your IDE/text editor open `www/index.php` and then change the code from `'/wp/wp-blog-header.php'` to `'/wp-blog-header.php'` _(e.g. remove the leading `/wp` from the filepath.)_

6. Rename `/www/../composer.json` to `/www/../composer.json.save` and delete `/www/../composer.lock` _(since you can no longer use Composer with this directory layout structure. Note: `composer.*` is in the project root directory.)_ 

7. That's it, you are done! WPLib Box now in _"Standard"_ WordPress directory layout.

#### The Script Approach

Or you can run this script, if you feel confident in doing so. First `vagrant ssh` to enter the box and then run the following commands:
    
    cd /var/www
    mv wp/*.* .
    
    mv wp/wp-admin/ .
    mv wp/wp-includes/ .
    mv content/ wp-content/
    
    rm -rf wp/
    
    sed -i "s#/wp/wp-blog-header.php#/wp-blog-header.php#" index.php
 
#### The CLI Approach _(Experimental)_ 

Or lastly you can try our experimental/alpha _"Inside-the-Box"_ [**Box CLI**](https://github.com/wplib/box-cli). After you make sure you have the latest version of WPLib Box just run:

	vagrant ssh
	box set-directory-layout-standard
	
Even better, if you want to switch back to _"Skeleton"_ layout, we have a command for that too:

	vagrant ssh
	box set-directory-layout-skeleton

