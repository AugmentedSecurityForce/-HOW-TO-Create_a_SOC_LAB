- [DOWNLOAD](#download)
- [VIRTUALBOX SETTING](#virtualbox-setting)
- [INSTALLATION](#installation)
- [CONFIGURATION](#configuration)

# DOWNLOAD
* Go to the [official site](https://www.pfsense.org/download/)
* Download the last stable version of the community edition

# VIRTUALBOX SETTING
* Create a new virtual machine

![setting01](Images/setting01.png)
![setting02](Images/setting02.png)
![setting03](Images/setting03.png)
![setting04](Images/setting04.png)
![setting05](Images/setting05.png)
![setting06](Images/setting06.png)

* Go to the VM properties
* In Network tab, activate 3 adapters
  * Used a paper to note the MAC ADDRESS of each cards, it can be usefull for future actions.

This will be the RED CARD (external network)
![setting07](Images/setting07.png)

This will be the GREEN CARD (internal network)
![setting08](Images/setting08.png)

This will be the orange CARD (dmz)
![setting09](Images/setting09.png)

* Launch the VM
  * It will ask you wich ISO Virtualbox must mount on the VM, load the pfsense one.

![setting10](Images/setting10.png)

# INSTALLATION
* Accept the copyright

![install01](Images/install01.png)

* Select "install"
  
![install02](Images/install02.png)

* Select your keymap
* Use the default partition (we're in a lab, we just need a firewall)
* Proceed with installation (no miror, no encrypt, nothing)
* Waiting

![install03](Images/install03.png)

* Don't load manual configuration

![install04](Images/install04.png)

* Reboot on the new system

# CONFIGURATION

Now, the server is power on with the new system
![conf01](Images/conf01.png)

* Select 1 to configure interfaces

![conf02](Images/conf02.png)
_Here, you can see the MAC ADDRESS and understand why i tell you to remember them.

* Select the RED INTERFACE for WAN
* Select the GREEN INTERFACE for LAN
* Select the last one (ORANGEE) for DMZ

![conf03](Images/conf03.png)

* Confirm

![conf04](Images/conf04.png)

* Select 2 to confogure the IP address
* Left the WAN interface as DHCP
* Select 2 to change the LAN interface
* Give it the IP and subnet you want, *the gateway must be "none"* !