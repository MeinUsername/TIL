#Setup a Virtualbox with Linux (Ubuntu 15)

- Create Machine with ca. 10 GB HDD
- Download image
- Mount image as CD.
- The new machine does not have paritions. So, when the partion selection screen (destination screen) appear, chooice *Something else* and create a new Partition
- Start the Installation

#After the Installation:

##Install / Configuration


### Change Screen resolution
This is necessary to change the screen resolution:
sudo apt-get install virtualbox-guest-dkms
### Setup shared folder
A shared folder can be configured with the virtual box manager. The Linux user needs to be added to the group vboxsf e.g.
```
sudo usermod -a -G vboxsf {Username}
```


### Install MySql
```bash
sudo apt-get install mysql-server mysql-client
```






