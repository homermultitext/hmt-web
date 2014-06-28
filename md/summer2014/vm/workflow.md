# Regular work flow with the HMT VM #

The folder where you cloned or downloaded the HMT VM is shared between your host operating system and the virtual machine.  On the virtual machine, the shared folder appears at `/vagrant`.  (This is where you also [clone your team's individual repository](edrepo.html).)

**1**.  Start up and connect to your VM if you have not already done so.

    vagrant up
    vagrant ssh

**2**. Change directory to the shared folder.

    cd /vagrant


**3**.  Make sure your have the most recent HMT material.
  
    sh hmt-refresh.sh


**4**.  Change directory to your editorial repository.

    cd YOUR-REPOSITORY-DIRECTORY


**5**.  Make sure you have your team's most recent material.

    git pull

**6**.  Work away!  See a summary of [automated tasks you can run in the HMT VM](scripts.html).