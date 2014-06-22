# Updating the HMT VM #

While the data and programs that the HMT VM automatically pulls in are constantly being updated, the virtual machine itself is modified much more rarely.  If you do need to update your installation of the virtual machine, follow these steps:

**1**.  Shut down the VM if it is running.

     vagrant halt

**2**. Update the VM files from the git repository.

    git pull

**3**.  Restart the VM.

    vagrant up


## Windows only ##

If your host operating  system is windows, make sure that `refresh-hmt.sh`  is formatted for your Linux VM as follows:

**4**.  Connect to the virtual machine.

    vagrant ssh

**5**.  Change to the shared directory, and convert Windows carriage returns to Unix newlines:

    cd /vagrant
    dos2unix refresh-hmt.sh


