title: Roadmap

# The WPLib Box Roadmap
At this point our _"Roadmap"_ is more of a _**work-in-progress**_ vision document as the project only has  [one sponsor](http://newclarity.net) and thus no dedicated staff so we really cannot commit to any timelines _(yet)._ 

_(But if you want to sponsor the project to help us reach a dedicated staff level, please [_contact us..._](http://slackpass.io/wplib))_

### You might be interested in:
Before you read about our planned milestones you might be interested in the following background:
+ [Audience](Audience) - Who is WPLib Box for?
+ [Approach](Approach) - What is our development approach _(**prior to version 1.0**)_?
+ [Features](Features) - What are the Features of WPLib Box?

## Milestones Planned for 1.0
The following are roughly in order of our plans to address:

- [New Installable Types](#new-installable-types)
- [Box Command Line Interface (CLI) Tool](#box-command-line-interface-cli-tool)
- [Deployment to Feature, Staging and Production Hosts](#deployment-to-feature-staging-and-production-hosts)
- [One Box for Many Projects](#one-box-for-many-projects)
- [Box Automated Testing](#box-automated-testing)
- [Box RESTful API](#box-restful-api)
- [Box Admin UI](#box-admin-ui)
- [Future Installable Containers](#future-installable-containers)
- [Eliminate use of Vagrant and VirtualBox](#eliminate-use-of-vagrant-and-virtualbox)

### New Installable Types
_"[_Installables_](Features#installables)"_ represent the WPLib Box's extension mechanism we use to quickly create new plugin-and-play functionality for WPLib Box, and to empower 3rd party developers to do the same. Currently Installables must be Docker Containers that add functionality to WPLib Box, and [offer one of the following classes of functionality](Features#current-installable-types): `webserver`, `dbserver`, `kvstore` and/or `processvm`.  

For our roadmap we plan to offer:

1. New classes of functionality for containers as we recognize additional use-cases and requirements and 

2. New types of installables not implemented as  containers. These could potentially be, but not limited to the following:
	
	a. WordPress plugins, especially those supporting SaaS solutions
	
	b. WordPress themes, potentially with bundled plugins
	
	c. Site blueprints containing plugins, themes and other files

	d. Additional commands for the Box CLI
	
	e. Command lines tools
	
	e. IDE and editor support
	
	f. Anything else that developers find they need to have the ultimate WordPress development environment.
	
### Box Command Line Interface (CLI) Tool
Currently WPLib Box has a [simple `box` command line tool](https://github.com/wplib/box-scripts) that is accessible when running an SSH shell inside the box, accessed via `vagrant ssh`. However we have yet to document that tool because we have plans for a completely redeveloped CLI tool. Our planned CLI tool will run both inside WPLib Box via SSH and also run the same commands from a Mac host terminal. In addition we plan to create an equivalent command line tool for Windows.

### Deployment to Feature, Staging and Production Hosts
A local development server is all well and grand but if you cannot deploy to your staging and/or production environments it leaves much to be desired.

Our goal is to **enable the deployment process to be trivial** for WPLib Box users.

Initially we plan to **just provide code deployment** where you would _push_ code from local development to staging to production and _pull_ database and files from production to staging to local development.

Later however we intend to address pushing changes from the database in local development up to staging and production, but we will not achieve that in the short term.

In addition, we envision supporting many different hosts as you need per project, e.g. staging, production and as many feature branch servers as you will ever need. 

And finally we intend to support hosts so that you can different hosting providers; e.g. you could deploy staging to a cheap shared Cpanel server and deploy production to an expensive Pagely account.

#### We are currently working on these:
- [Pantheon](https://pantheon.io/features/wordpress-hosting-on-pantheon) and [WPEngine](https://wpengine.com/)

#### We will probably tackle these next:
- [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-use-the-wordpress-one-click-install-on-digitalocean), [Linode](https://www.linode.com/docs/websites/cms/how-to-install-and-configure-wordpress), [Google Compute Engine](https://console.cloud.google.com/launcher/details/click-to-deploy-images/wordpress), [Amazon Web Services](https://aws.amazon.com/getting-started/tutorials/launch-a-wordpress-website/), [CPanel Server](https://cpanel.com/), [Vultr](https://www.vultr.com/docs/one-click-wordpress), [Kyup](https://kyup.com/tutorials/install-wordpress/)

#### We will address these when and if clients need them or vendors support us financially:
We could also add deployment support these if support is contributed by one of our users or by the vendors themselves.
- [Cloudways](https://www.cloudways.com/en/wordpress-cloud-hosting.php)
- [Pagely](https://pagely.com/), [Kinsta](https://kinsta.com/), [Pressable](https://pressable.com/), [Presslabs](https://www.presslabs.com/), [WebSynthesis](http://websynthesis.com/), [Flywheel](https://getflywheel.com/why-flywheel/), [Pressed](https://www.pressed.net/)
- [SiteGround](https://www.siteground.com/wordpress-hosting.htm), [Liquid Web](https://www.liquidweb.com/wordpress/), [DreamHost](https://www.dreamhost.com/hosting/wordpress/), [Media Temple](https://mediatemple.net/webhosting/wordpress/), [GoDaddy](https://www.godaddy.com/hosting/wordpress-hosting), [Lightning Base](https://lightningbase.com/)
- [WordPress VIP](https://vip.wordpress.com/), [Microsoft Azure](https://docs.microsoft.com/en-us/azure/app-service-web/app-service-web-create-web-app-from-marketplace) 

### One Box for Many Projects
Multi-project is our _"holy grail"_, and that which we cannot reach version 1.0 without. 

Currently WPLib Box is a single project box. But our plan is to move to multi-project where each WordPress installation is a project, which can be a WordPress single-site or multisite install.

Our initial reason for creating WPLib Box is the fact that VVV was very heavy with more than just a few site and so we have a lot of engineering to complete to ensure that WPLib Box continues to feel as light as it does while still being able to support a large number of site in current and prior development.

### Box Automated Testing
As developers we know that test-centric development is a best practice, even if we don't always do it. And there are tools like [PHPUnit](https://phpunit.de/), [Behat](http://behat.org/en/latest/) and [Codeception](http://codeception.com/),  that leave little excuse for not using automated testing in your projects

But as far as we know there are not standard testing frameworks for solutions like WPLib Box because there are so few people actually building solutions like WPLib Box.  So we intend to figure this out and probably build our own tools in order that we can deliver new releases which are fully tested in advance.

### Box RESTful API
We envision WPLib Box as containing a set of services that allow very simply configuration and administration of the most common use-cases. For example, adding a project to the box with its own hostname and WordPress installation should be trivially easy, not require the user possess any system administration skills, and it should both _"Just work"_ and _"Never break."_  

Clearly if we provided just a CLI and an end-user admin UI we would enable such configuration and administration but we believe we should go one step better and implement a RESTful API. This API will enable code running on a host computer to call into a box to perform any and all configuration and administration tasks This will empower users and 3rd party developers to create tools for WPLib Box that we'd never envision or simply that we have yet to implement.

Matter of fact, we intend to implement our HOST CLI functionality by having it call our RESTful API which will in turn delegate to the same CLI running inside of WPLib Box. When run outside the box the CLI will call the API and when run inside the box the CLI will actually execute the task.  We also intend to develop our admin user interface using this API.  Or as so many other tech companies like to say, we plan to _"eat our own dog food."_

### Box Admin UI 
After we have the majority of the `box` CLI tool and the majority of the RESTful API completed we intend to develop an admin user interface for the box using GitHub's [Electron](https://electron.atom.io/) platform for the Mac and Windows desktop app, and [React](https://facebook.github.io/react/) for the Single Page App functionality.  

This Admin UI will mirror the functionality provided by the Box CLI and the RESTful API with the addition of any functionality required that is specific to the Mac and Windows host.

### Future Installable Containers
The following are installable containers we have discussed and/or considered. Depending on user interest, we might implement these ourselves at some point, or adopt installables created by our users or the solution's vendor.

- [OpenLiteSpeed](https://www.litespeedtech.com/open-source/openlitespeed) Web Server
- [Percona Server](https://www.percona.com/software/mysql-database/percona-server) for MySQL
- [Gearman](http://gearman.org/)
- [ElasticSearch](https://www.elastic.co/products/elasticsearch)
- [ZeroMQ](http://zeromq.org/)
- [RabbitMQ](https://www.rabbitmq.com/)
- [PHPUnit](https://phpunit.de/)
- [Behat](http://behat.org/en/latest/)
- [Codeception](http://codeception.com/)

If you don't see what you need on this list, please [**nominate a potential future installable**](https://github.com/wplib/wplib-box/issues/new). And if you are interested in developing it, please be sure to mention then, and also please [join our Slack](https://slackpass.io/wplib) so we can reach out to you to discuss directly.

We do not use the term single-site vs. multisite because we do not want to confuse with WordPress Multisite functionality; our current single project box can support WordPress Multisite just fine.  

### Eliminate use of Vagrant and VirtualBox

Our final version 1.0 goal is to move beyond Vagrant and VirtualBox and run within our own self-contained Linux environment that can run as seamlessly as running any desktop application might be.  This is the last step we will tackle before we are ready to release version 1.0.

## The Open Source WPLib Box; Always Free
Lastly, our goal for for WordPress developers to **love** WPLib Box and _willingly choose it over any other local development solution and for that we know that we will need to ensure our open-source WPLib Box software is always free to individual developers.

And while we do plan to build a revenue-generating business out of WPLib Box, we pledge to only charge for those things where we have direct hard costs and/or where the benefits-of-use accrue to the non-developers; the project managers, the business people and/or the executive team, not the things that only benefit individual developers. One such example might be tools for secure team development on WPLib Box. Frankly we are building it not quite sure what the business model will be but confident if we build a tool that all WordPress developers love we will find a way to fund our operations.

