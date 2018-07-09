title: project.json

# NOT FINISHED
## `project.json`

The current version of WPLib Box is configured using a project-specific `project.json` file which you can find in the 
root of your project directory.  The default value for `project.json` for version `0.17.0` is:

    {
        "stack" : {
            "wordpress/dbserver":	 "wplib/mysql:5.5.60",
            "wordpress/webserver":	 "wplib/nginx:1.14.0",
            "wordpress/processvm":	 "wplib/php:7.1.18",
            "wordpress/cacheserver": "wplib/redis:4.0.9",
            "mkdocs/webserver":	 "wplib/mkdocs:0.15.3",
            "box/mailsender":        "wplib/mailhog:1.0.0",
            "box/webproxy":		 "wplib/proxy:1.14.0",
            "box/sqladmin":		 "wplib/adminer:4.6.2"
        }
    }


