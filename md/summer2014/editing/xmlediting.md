# XML editing #


## Guide to TEI usage ##



For details of markup, see the Homer Multitext project's *Guide for Editors*.  (2013 edition available [here](http://www.homermultitext.org/hmt-docs/HMTstyle-preview.pdf).)


## General work flow ##


Your general work flow should follow this pattern:

1. Refresh all repostiories in your virtual machine.  (To start your VM: `vagrant up`;  to connect to it:  `vagrant ssh`; to refresh all repositories: `cd /vagrant` and then `sh refresh-hmt.sh`.)
2. Using oXygen running in your host operating system (e.g., Mac OS, Windows), edit your XML texts.
3. In your VM, verify your editing (`sh verify.sh`)
3. If your work looks good, save changes in your local clone of the repository (`git add FILENAME` and then `git commit`)
4. Push your changes back to github (`git push`)



## Possible complications ##

If you cannot find an identifier for a personal name or place name in the [HMT project authority lists](https://github.com/homermultitext/hmt-authlists/tree/master/data), then file an issue in the appropriate issue tracker, [following the instructions in this guide](submittingAuthListIssues.html).



