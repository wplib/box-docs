title: Components

# NOT FINISHED
## Components in WPLib Box 

WPLib Box defines a concept called a _"Component"_ 

!!! note 
    The following describes our 1.0 vision for WPLib Box.<br>
    Though not everything described below is implemented we plan to be feature-complete before 2019. 

## Categories

In general Components will fall into one or more of these categories:

1. **Service Containers**: Service apllications running in Docker containers; _i.e. web servers, 
   database servers, process VMs (e.g. a PHP version), etc._
1. **Executable Containers**: Compiled binaries running inside of a Docker container; _i.e. Command-line versions of PHP, Python 
   and Ruby as well tools like Git and SVN, etc._  
1. **Scripts**: Executable scripts that run by invoking an executable container; _i.e. Composer, PHPUnit, WP-CLI, PHP-CodeSniffer, etc._
1. **Source**: Source code files; _i.e. WordPress core, plugins, themes and PHP libraries as well as collections of those files we will call Blueprints._
1. **Data**: Data files; _i.e. MySQL dumps, XML files, JSON files, etc._
1. **Media**: Media files; _i.e. Image files, video files, PDF files, etc._
 

## Requirements

Each component has a _"Named Type"_ and each component must _**implement**_ the _"Interface"_ defined by its named type.

### Named Types

### Interfaces







# WPLib Box Installables

Installables are a method to add additional functionality to WPLib Box. These packages can include anything, and any user can create a package.

### Current Installable Types
All of the following Installable Types are implemented via a Docker Container and supplied 
- `container/webserver` - An **HTTP Web Server** that runs on Linux that provides sufficient features to serve WordPress websites, such as Nginx.
- `container/dbserver` - A **MySQL-compatible Database Server** that runs on Linux that can serve databases for WordPress websites
- `container/kvstore` - A **Key-Value Store** typically used for persistent object caches in WordPress, such as Redis or Memcached
- `container/processvm`  - A **PHP-style language engine** used to execute WordPress source code.

### Currently Supported Installables
WPLib Box can currently compose an operating _"stack"_ from the following Installables _(the first one listed in each category is the [**_default installable_**](/wplib/wplib-box/blob/master/project.json#L2))_ when you first install WPLib Box:

|Category|Default Installable | Also Available  |_"Installable Type"_|Notes|
|--------|--------------------|-----------------|--------------------|-----|
|<nobr>**Web Server**</nobr>|[Nginx](https://nginx.org/en/)|[Apache](https://httpd.apache.org/) and [Caddy](https://caddyserver.com/)|`container/webserver`||
|**DB Server** |[MySql](https://www.mysql.com/products/community/) |[MariaDB](https://mariadb.org/about/)|`container/dbserver`||
|**KV Store**|[Redis](https://redis.io/)|[memcached](https://memcached.org/)|`container/kvstore`||
|**<nobr>Process VM</nobr>**|[PHP 7.0](http://php.net/releases/7_0_0.php)|[<nobr>PHP 7.1</nobr>](http://php.net/releases/7_1_0.php) and [<nobr>PHP 5.6</nobr>](http://php.net/releases/5_6_0.php) |`container/processvm`|PHP 7.0 and 5.6 are _(currently)_ implemented in Docker containers but PHP 7.1 has been installed directly to Linux while we wait for an official Docker PHP 7.1 container.|

**Disclaimer:** _Currently all except Caddy and `container/webserver` are not actually implemented as installables, but instead installed directly. However it is our intention to convert them all to installables in the near future._

### How Installables Work
Installables are listed in the [`project.json` file](/wplib/wplib-box/blob/master/project.json) for each project that uses WPLib Box. In this JSON file is a list of services that will get automatically configured and made to run whenever `vagrant up` is run. Vagrant delegates to `box startup` which it runs inside in the Linux box _(specifically this script does not run in the Windows or macOS host computer, it runs via SSH tunnelling in WPLib Box.)_

If WPLib Box does not find that the installable has been previously installed in the current WPLib Box it reaches out to the Internet and downloads and installs the installable, and then ensures that it is running for the current project. This approach allows **easy stack sharing during development among team members on multi-developer project**, and it makes it **easy for individual developers to pick of a prior project** without having the spend time recreating the previously used development environment.

Note that we expect the exact details of how installables work will to evolve significantly before we reach version 1.0 so we'll wait until things settle down before document them in detail. 

### Anatomy of a Docker Container Installable.
+ `installable.json` - A file at the root level of the repository that defines the installable package.
+ `commands` directory - This subdirectory contains commands that can be executed by the guest CLI.
+ `README.md` (optional) - This should detail how to install the package and the CLI commands made available.

#### `installable.json` Contents
This file is simply a collection of JSON objects that define the package.

#### JSON Object Properties

<table>
<thead>
<tr>
<th>Property Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>name</code></td>
<td>This is the name of the installable. This should be in human readable form, <em>e.g. <code>My Super Cool Installable</code></em>.</td>
</tr>
<tr>
<td><code>version</code></td>
<td>The installable version. This should following Semantic Version rules, <em>e.g. <code>0.1.0</code></em>.</td>
</tr>
<tr>
<td><code>type</code></td>
<td>Each package has both a major and minor type. The major type defines the role the installable plays in the box, <em>( e.g. <code>webserver</code> )</em>. The minor type is the implementation of the installable, <em>( e.g. <code>container</code> for a Docker container )</em>. Currently, only Docker container minor type is supported.</td>
</tr>
<tr>
<td><code>download</code></td>
<td>This is the source repository of the installable, <em>( e.g. <code>wplib/my-super-cool-installable</code> )</em>. Currently, only GitHub repositories are supported.</td>
</tr>
<tr>
<td><code>containername</code></td>
<td>This is the name to use for the Docker container. It <strong>MUST</strong> be unique, <em>( e.g. <code>mysupercoolcontainer</code> )</em>.</td>
</tr>
<tr>
<td><code>website</code></td>
<td>This is the URL for the installable. This could be either the GitHub repository, or a link to a site or page dedicated to information about the installable package.</td>
</tr>
<tr>
<td valign="top"><code>contains</code></td>
<td><p>This a JSON object with the following property/value pairs: <code>type</code>, <code>version</code>, and <code>website</code>. If you were to create a installable for ElasticSearch, this object might be as follows:</p> 
<pre>contains:{ 
   "type": "service/linux", 
   "version": "5.4.0", 
   "website": "https://github.com/elastic/elasticsearch" 
}</pre></td></tr>
</tbody>
</table>

## Container Hosting
The Docker containers used by our installables are hosted at the [WPLib account on Docker Hub](https://hub.docker.com/u/wplib/).  


