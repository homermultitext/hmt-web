# Working with a shell in a POSIX system#


## Background ##


There have been many operating systems to run on all kinds of computing devices over the past half century, but none has been more widely used than UNIX.  Astonishingly, while originally designed in the late 1960s, UNIX is still in use today, and on more machines than ever before:  every iPhone and iPad runs a version of UNIX, for example.

The fundamental UNIX interfaces have become so important that the IEEE has defined the POSIX standard to specify what essential interfaces constitute a fully POSIX-compliant operating system.  In addition to various UNIX distributions, this includes most Linux distributions.  When you become familiar with a standard command-line shell for POSIX systems, therefore, you are learning a system you can use identically on most of the internet's web servers, a personal Macbook,  or a an Android phone.  

![bash shell on Android phone][2].  

Even more remarkably, most of the shell commands you regularly use are identical to what you could have used entered on a teletype  PDP-11.

![Dennis Ritchie and Ken Thompson][1] (source:  <http://cm.bell-labs.com/cm/cs/who/dmr/picture.html>)

These brief notes will show you a few shell commands you can use to interact with a POSIX-compiliant system, whether you are using a terminal application on your own computer, connecting to a remote machine using the secure shell program `ssh`, or running a virtual machine.  Explore on your own, and let Google help you when you need more information.


[1]: http://cm.bell-labs.com/cm/cs/who/dmr/kd14.jpg

[2]: http://shot.holycross.edu/bashdroid.jpg



## Working in your VM ##

The Homer Multitext project's virtual machine for editors runs Ubuntu Linux, a POSIX compliant system.  As you look through these notes, try out commands in your VM to see what they do.  If you haven't already started up and connected to your VM, do that (`vagrant halt`, then `vagrant ssh`).  Then, within your virtual machine, change directory to the shared directory you can also see in your host operating system:  `cd vagrant`.  That directory includes some sample data files you can use to practice with these bash commands.


## Some basic shell commands ##


One of the first commands you should become familiar with is `man`, which lets you browse manual pages for a command.  Try entering `man pwd`  to find out what the `pwd` command does.  If you want to find out more about `man` itself, just enter `man man`!


## Directories and files ##



To navigate your way through your files and directories using the command line, you will regularly use the following commands:

- `ls`
- `pwd`
-  `cd`

Figure out how to use these commands to:

- Find out where your home directory is on the virtual machine (that is, what is the full path to it?).  When you connect to a remote machine with `ssh`, your working directory is initially your home directory.  
- Find out what files are in the `sampledata`  directory.  
- Change your working directory to the sampledata directory, then change back to your home directory.

Two useful additional commands you can use to navigate your file system are `pushd` and `popd`.  Repeat the last change of directories and return to your home directory using them.

The bash shell also allows you to refer to a file or files with a shorthand pattern notation known as file globbing.  The most common file globbing shorthand is the asterisk, which means "match any characters".  A shell command like `ls *.txt` therefore will list all files ending with the extension `.txt`.


## Viewing and manipulating contents of files ##



You have already used `man` to view the contents of manual pages.  `man` actually relies on a separate pager to browse through files, by default, a program named `more`.  To display or print the full contents of a file, you can use `cat`.

- use `more` to browse the file `sampledata/tokensfile.txt`
- use `cat` to print the full contents of the same file

You can get summary information about a file with the `wc` program, which, despite its name, counts more than words.  Read the `man` entry on the various options for `wc`, then use it to:

- count only the number of lines in the sample data file
- count only the number of characters in the sample data file

The sample data file containsdata in two columns, separated by a tab.  The two columns sequentially identify words in the first 21 lines of the *Iliad*, and analyze the word as either a lexical token, or a named entity (a proper noun or adjective, such as a personal or geographic name).  If you only wanted the word list, you could use the POSIX `cut` command to select the first **f**ield, or column, like this:

    cut -f1 <FILENAME>

There is a symmetric `paste` command that aligns data from two or more files in columns.

If you want to search through a file, `grep` will find and print lines matching a pattern.  You could find only the words classified as named entities with this command:

    grep namedEntity sampledata/tokenfile.txt

If you want to negate the search, and find only lines *not* matching a pattern, you can include the `-v` flag.  This would find all lines that do **not** include the pattern "namedEntity"

    grep -v namedEntity sampledata/tokenfile.txt

If you would like to make some kind of global change to a file, you can use `sed`, a "stream editor".  You can do an enormous range of things with `sed`, but substituting one pattern for another is one of the most important.  The basic syntax looks like this:

    sed 's/OLD/NEW/' <FILENAME>

You can read this as a command to `sed` to **s**ubstitute NEW wherever you find OLD in the named file or files.  Try this on your test file:

    sed 's/urn:cts:greekLit:tlg0012.tlg001://' sampledata/tokenfile.txt

Can you predict what this will do?  Run it and compare the results to what you would see if you used `cat` or `more` on the file.

Both `sed` and `grep` use a very powerful pattern matching syntax called regular expressions.  You can learn [more about regular expressions](re.html) in a later section of this thread, but we'll introduce two details of regular expression here that are very similar to the file globbing you already saw.  The period means 'match any character', and the asterisk means "zero or more occurrences of the previous character."  We can alter the previous pattern to match *zero or more occurrences of any character up to the '@' sign*  like this:

    sed 's/.*@//' sampledata/tokenfile.txt

The result is a list just of the words, and their classification.

A further common task is to sort a file.  You can do this with the simply named `sort` program.  We'll look at examples in the next section.

## I/O redirection ##



Some of the previous commands (especially `sed` and `grep`) offer a complex set of options, but in its simplest, default form each does a single task simply and well.  This reflects a conscious approach to design that runs through the original UNIX system.  Of course each simple task would be much more valuable if it could be combined with other simple tasks, and the designers of UNIX planed for this.  In the examples above, each program read some input from a file, and wrote  to a standard output directed to your terminal.  You can redirect your output to a file using the "greater than" sign, `>`.  Try this:

    cut -f2 sampledata/tokenfile.txt > classifications.txt
    cat classifications.txt

Now we could run a program on just the classifications, e.g.,

    sort classifications.txt > classifications-sorted.txt
    cat classifications-sorted.txt

One further useful program for working with sorted data is `uniq` (Yes, the command name is only four letters long.  When Ken Thompson, one of the original designers of UNIX, was asked what he would do differently if he were redesigning UNIX, he said of the similarly laconic command name `creat`, "I'd spell `creat` with an 'e'." )  Run this:

    uniq classifications-sorted.txt

This is a very useful piece of information:  it answers the question, "What are the unique values for the classification of tokens in the sample data set?"  We created a lot of temporary files to get there, though.  POSIX system also let us redirect input/output streams using the "vertical pipe" character, '|', between two commands.  The pipe means that the output of the first command serves as the input to the following command, so we could reduce our query for unique values to a single line:

    cut -f2 sampledata/tokenfile.txt | sort | uniq

Try using combinations of commands you've learned to answer each of the following questions with a single, piped command line:

- *How many* distinct values are there for the second column of the sample data file?
- What are the list of passage references and words for the first 21 lines of the *Iliad*? (That is, strip off the leading information at the beginning of the line, and throw out the second column altogether.)
- Extract a list of just the words (as you did above with sed), and find a sorted list of unique words in this passage.
- Count how many unique words occur in this passage.
- Count how many total words occur in this passage.



## History ##



`bash` also keeps a history of commands you have used recently, and provides a number of commands and shortcuts that take advantage of this.  You can:

- use the `history` command to see what you have done
- on most terminals, use  up and down arrows to back or forward through your command history
- repeat a command using the exclamation point.  `!!` repeats the previous command;  `!` before a number repeats that numbered command (using the number seen in `history`).
-  substitute part of the preceding command string using the caret (^).  If you mistakenly entered `hisstory`, you could correct that by entering `^ss^s`, that is, "replace 'ss' with 's'".

[3]: vagrant.html

[4]: re.html