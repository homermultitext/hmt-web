# Cloning your editorial repository in the HMT VM #



The HMT VM includes all the shared programs and data you need to edit material for the Homer Multitext project. In addition to this, you will need to install your team’s individual editorial repository in the VM.

**1**. Start up your VM, and connect to it, if you have not already done so.

    vagrant up
    vagrant ssh
    
**2**. In the VM, change directory to the shared folder.

    cd /vagrant
    
**3**. Clone your repository.

    git clone YOUR-REPOSITORY-NAME

## Windows only ##


If your host operating system is windows, make sure that shell scripts are formatted for your Linux VM:

**4**. Convert Windows carriage returns to Unix newlines:

    dos2unix *.sh


