# hmt-web

Source repository for the Homer Multitext project web site, <http://www.homermultitext.org>.

This repository uses the `cdweb` library to generate a web site from source pages written in markdown.

Documentation in markdown format should be kept in the md directory (or its descendants) in files with extension `.md`

To build a web site, run

    gradle web

The resulting web site will be placed in `build/web`.

 
## Editing a web site ##

- Put markdown files within the directory defined by the `srcdirectory` property (including its descendants) (default: `md`)
- Put css files within the directory defined by the `cssdirectory` property (including its descendants) (default: `css`)
- Configuration values are set in files contained within the `srcdirectory` tree and named `web.properties`.  Settings in `web.properties` cascade to the html conversion of all markdown files contained within the site, unless overridden by a descendant `web.properties` file, so if you want (e.g.) to add a further CSS stylesheet to each page modify the `head` property in the top-level `web.properties` file to include a link to the new CSS stylesheet, and it will cascade down to every web page on your site.


## Building a web site ##

Run 

    gradle web

The first time you run this may be slow, since gradle will have to find and download the mdweb and citedown libraries.  The web site will be built in the directory `build/web`.

