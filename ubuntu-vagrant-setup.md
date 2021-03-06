#Notes
Commands to get the virtual box and vagrant installed on Ubuntu 16.x
```
sudo apt-get update
sudo apt-get install virtualbox
vboxmanage  --version
sudo apt-get install vagrant
vagrant  version
```

Beginners commands
```
sudo vagrant init
#modify the Vagrantfile 
sudo vagrant up
sudo vagrant status
sudo vagrant ssh 
#login into the new VM created. 
sudo vagrant halt
sudo vagrant destroy
```

Creating Vagrant Boxes
```
vagrant package --output /path/to/<boxname>.box
vagrant box remove atlas-path/<boxname>
vagrant box add atlas-path/<boxname> /path/to/<boxname>.box

Example:
vagrant package --output k8s-1.6.2-2017050901.box
vagrant box remove openebs/k8s-1.6
vagrant box add --name openebs/k8s-1.6 k8s-1.6.2-2017050901.box 
```

#Reference
* [Installing Vagrant and Virtual Box] (https://www.olindata.com/blog/2014/07/installing-vagrant-and-virtual-box-ubuntu-1404-lts)
* [Vagrant docs] (https://www.vagrantup.com/docs/)
* [Bento boxes] (https://github.com/chef/bento)
