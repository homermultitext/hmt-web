# Installing the HMT VM #



## 1. Download and install the prerequisites ##

- vagrant: <http://www.vagrantup.com>
- virtualbox: <https://www.virtualbox.org/>

## 2. Get the VM files ##

If you have `git` on your system:

    git clone https://github.com/homermultitext/hmt-vm


If you do not have `git`:

- point a web browser at <https://github.com/homermultitext/hmt-vm>
- use the "Download ZIP" button to download the current version. (See [an illustration][dl] of the "Download ZIP" button.)
- if your browser does not automatically unpack the zip file for you, unzip it (e.g., by dragging the zip file where you want to unpack it, then double clicking it)


## 3. Install the machine ##

**A**.  In a terminal, change directory (`cd`) to wherever you put the VM files.  (E.g., if you cloned or unzipped the files on your Desktop, `cd Desktop/hmt-vm`.)

**B**. Then, run

    vagrant up

**C**. Go get a cup of coffee while the machine builds.




[dl]: http://www.homermultitext.org/images/download-hmt-vm.png