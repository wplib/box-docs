title: MkDocs
#NOT FINISHED

## Using MkDocs with WPLib Box

While you certainly _can_ install MkDocs on your [host computer](/glossary/#host-machine) and use it with your 
WPLib Box project, hopefully you won't have to as  we've ==implemented MkDocs within of WPLib Box==.

## Using MkDocs
[MkDocs](http://mkdocs.org/) allows you to both ==dynamically _**serve**_ documentation== from 
[Markdown](https://www.markdownguide.org/) files while you are writing your docs _(just like you can dynamically 
serve PHP files from your web server)_, and then MkDocs allows you ==to _**build**_ a static website== from those 
Markdown files for hosting your docs on your web server.  

### Dynamically Serving Markdown 
WPLib Box automatically serves the Markdown files contained in your project's `/mkdocs` directory to `docs.wplib.box` 
in your browser _(or to whatever `docs.` subdomain is created by `Vagrantfile` when you add your own domain name in 
the `HOSTNAME` file.)_  

### Write docs in Markdown 
MkDocs allows you to write rich documentation in Markdown &mdash; great for documenting 
reusable plugins and themes &mdash; ==that you can then version control!== 

and view using the MkDocs built-in server which WPLib Box automatically configures


to serve from your project's '`/mkdocs  

 in a root or subdirectory of your 
web server containing the HTML, CSS and images that comprise a static copy of your documentation.

reads the `/mkdocs.yaml` file which you can learn how to configure [**here**](https://www.mkdocs.org/user-guide/configuration/).
If you use our chosen default `material` theme you can also learn to configure [**here**](https://squidfunk.github.io/mkdocs-material/customization/)
and [**here**](https://squidfunk.github.io/mkdocs-material/extensions/admonition/). 
  
### Generating 

 
so to use it you first 
[SSH into WPLib Box](/docs/tutorials/secure-shell) and then run your MkDocs command, for example:

    vagrant ssh
    MkDocs install

## Implementation
Our implementation of MkDocs follows WPLib Box's [philosophy of containerization](/philosophy/#functionality-should-be-containerized) 
and is thus implemented with our [own Docker container](https://hub.docker.com/r/wplib/MkDocs/).  

Our `MkDocs` command is itself is a Bash script which is designed to invoke the MkDocs container and that script 
can be found at `/opt/box/bin/mkdocs` after you `vagrant ssh` into WPLib Box.  
 
 
## Current Limitations

- Running `mkdocs` almost always starts `mkdocs serve` which is not particularly useful, especially if you are 
trying to run `mkdocs --version` or similar. [We plan to fix this very soon](https://github.com/wplib/wplib-box/issues/481).

- Some commands may have issues. If you find this to be the case ==please [contact our support](/support/)== 
to let us know so we can address sooner than later.
