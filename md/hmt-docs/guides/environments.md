# Environments for editing #


Since all editorial work for the HMT project is managed in git version control repositories, it is possible to edit in a repository and keep it up to date from any environment that supports git.  Because we want to validate our work as early and often as possible, a normal organization of work for the HMT project would use three different environments:

## web interface to a git repository on github ##

Since github parses `.csv` files, and comments on syntax errors with extremely clear diagnostic messages, we recommend using a web browser to edit all `.csv` files in a repository on github.

## oXygen XML editor on your personal computer ##

oXygen XML editor is the best XML editor we have experience with.  It validates your files as you work, and offers a number of  shortcuts that are very handy in editing complex XML documents.  Most HMT contributors will want to run a copy of oXygen directly on their personal computer.


## HMT virtual machine for valdiation ##

The HMT project's automated validation system can be built on any POSIX-compliant system where the Perseus project morphological parser, morpheus, can be compiled.  For most HMT editors, the easiest way to do this is to run the HMT virtual machine using Vagrant and Virtual Box.

## Putting the whole package together ##

The HMT virtual machine shares a folder with your personal computer's operating system (the "host" machine).    This means that if you clone your repository of editorial work in the shared directory, you can use oXygen from your personal computer's operating system to edit XML files, use a web browser from anywhere to edit `.csv` files on github, and run validating scripts in the virtual machine to test the same files.  While it may seem confusing at first to work on the same files in three different environments, each environment offers distinct advantages for different parts of the HMT editorial process (validating the syntax of `.csv` files, validating the syntax of XML files, and running validation scripts to test the contents and relations of the entire repository).

## What if I want to do everything on my personal computer and get rid of the virtual machine altogeher? ##

Feel free to install everything you need to run the HMT validation suite on your personal computer if you prefer, and share any documentation or notes you compile on how to do so.  In practical terms, the morpheus parser may be impossible to build on current Windows or Macintosh operating systems, so that's probably what you should test first.  If you run a 64-bit Linux operating system, morpheus should compile out of the box, and the rest of the requirements for running the HMT validation system, `hmt-mom`, are straightforward to install.


