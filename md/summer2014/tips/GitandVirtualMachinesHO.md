# How to Work Using Git #

A local machine is the physical machine on which you working. When you start up and connect to a virtual machine, you are no longer working on your host operating system, but a virtual Linux machine. If you do not start up a virtual machine, you are working in the operating system your computer comes with (e.g., Mac OS or Windows).   Because the virtual ("guest") machine and local ("host") machine share a folder, you can work on the files within that folder using either operating.  You can edit files using oXygen on your host machine, for example, but use the virtual machine to run automated tests.

## Working Just on a Local Machine ##

Normal workflow typically runs like this:

1. `cd PathwayToYourRepository` (puts in the directory in which you want to work)
2. `git pull` (updates your repository to the most current version hosted on github)
3. you may now edit as much as you like, save when you are done
4. `git status` (shows you which files you have modified
5. `git add FilesYouHaveModified` (you want to `git add` every file you have modified during your editing)
6. `git commit` (to commit changes you have made to your local repository. You will be prompted to enter a short message explaining what you have done. If you are configured for TextEdit or Notepad++ you `save` and `quit` when you are done entering your message)
7. `git push` (will send all your edits to the repository hosted on github so that anyone else can pull those updates and continue working. You will be prompted to enter your github username and password).

Note: You can edit some files straight in the web browser on github. You do not need to do any adding, committing, or pushing after finishing here, but make sure if you are about to edit files locally or run any validation scripts on your machine that you pull those edits before beginning.

## Working In a Virtual Machine ##

1. `cd PathwayToYourRepository/hmt-vm` (will get you to your virtual machine)
2. `vagrant up` (starts up the virtual machine)
3. `vagrant ssh` (connects to the virtual machine via a secure shell)
4. `cd /vagrant` (puts you in shared directory on the virtual machine)
5. `sh refresh-hmt.sh` (checks for updates to the virtual machine)
6. `cd YourRepository` (puts you in the copy of your repository in the virtual machine)
7. `git pull` (updates your repository to the most current version hosted on github)
8. You may now work on editing in the virtual machine. Be sure to save when you are done.
9. `git status` (shows you which files you have been editing in the repository)
10. `git add FilesYouHaveModified` (you want to `git add` every file you have modified during your editing)
11. `git commit` (to commit changes you have made to your local repository. You will be prompted to enter a short message explaining what you have done. The virtual machine runs a Linux and will not be configured to run your usual editor.  You can instead include a commit message on the command line in the following format:  `git commit -m "YourCommitMessage"`.)
12. `git push` (will send all your edits to the repository hosted on github so that anyone else can pull those updates and continue working. You will be prompted to enter your github username and password).
13. `exit` (takes you out of the secure shell)
14. `vagrant halt` (stops running the virtual machine)

## Working in Both Local and Virtual Machines ##
1. `cd PathwayToYourRepository/hmt-vm` (will get you to your virtual machine)
2. `vagrant up` (starts up the virtual machine)
3. `vagrant ssh` (connects to the virtual machine via a secure shell)
4. `cd /vagrant` (puts you in the shared directory on the virtual machine)
5. `sh refresh-hmt.sh` (checks for updates to the virtual machine)
6. `cd hmt-YourRepository` (puts you in the copy of your repository in the virtual machine)
7. `git pull` (updates your repository to the most current version hosted on github)
8. You may now work on editing in the virtual machine. Be sure to save when you are done.

**You may find that you don`t like committing and pushing in the virtual machine. In that case follow these instructions**

9. In a new Terminal window, `cd PathwayToYourRepository/hmt-vm/hmt-YourRepository` (will put you in the local copy of your repository within the virtual machine)
10. `git status` (shows you which files you have been editing in the repository)
11. `git add FilesYouHaveModified` (you want to `git add` every file you have modified during your editing)
12. `git commit` (to commit changes you have made to your local repository. You will be prompted to enter a short message explaining what you have done. If you are configured for TextEdit or Notepad++ you `save` and `quit` when you are done entering your message)
13. `git push` (will send all your edits to the repository hosted on github so that anyone else can pull those updates and continue working. You will be prompted to enter your github username and password).

**Don`t forget to go back to your Terminal window with the virtual machine and shut it down**

13. `exit` (takes you out of the secure shell)
14. `vagrant halt` (stops running the virtual machine)

## Other Helpful Terminal Commands ##

`open .` (opens in Finder or Files your current working directory)
`pwd` (shows you the current working directory)
`up arrow` (lets you cycle through previous commands)
`tab` (will autocomplete your commands as far as they are unambiguous, helpful for very long, difficult to spell commands)
`..` (takes you back one level in your working directory)
`ls` (lists what is in the working directory)
