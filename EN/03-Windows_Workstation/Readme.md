- [DOWNLOAD](#download)
- [VIRTUALBOX SETTING](#virtualbox-setting)
- [INSTALLATION OF WINDOWS](#installation-of-windows)
- [CONFIGURATION OF WINDOWS](#configuration-of-windows)
- [ADD YOUR WORKSTATION TO THE DOMAIN](#add-your-workstation-to-the-domain)

# DOWNLOAD
* Download the [tool offer by Microsoft](https://go.microsoft.com/fwlink/?LinkId=691209)
* Launch it
* Accept the software licence
* Select "create a installation support" to make an ISO
* Select the english language

![download1](Images/download1.png)

* Select "ISO file"
* Save the file on your computer

# VIRTUALBOX SETTING
* Create a new virtual machine

![vm01](Images/vm1.png)
![vm02](Images/vm2.png)
![vm03](Images/vm3.png)
![vm04](Images/vm4.png)
![vm05](Images/vm5.png)
![vm6](Images/vm6.png)

* Go to the VM properties
* In Network tab, change the configuration to use internal network : GREEN

![vm7](Images/vm7.png)

* Launch the VM
  * It will ask you wich ISO Virtualbox must mount on the VM, load the Windows Server one.

# INSTALLATION OF WINDOWS
* Select the English language to install.
  * The other setting can be adjust with your favorite configuration but in IT you must install Windows in English !

![install1](Images/install1.png)

* Select "install now"
* Select "i don't have a product key" (or enter the one you have)

![install2](Images/install2.png)

* Select Windows 10 Pro version

![install3](Images/install3.png)

* Accept the license terms
* Select a custom install

![install4](Images/install4.png)

* Select the only drive you have and select "Next"

![install5](Images/install5.png)

* Waiting for install and reboot
* Select your region
* Select your keyboard layout
* Select "I don't have internet" in the left bottom corner

![install6](Images/install6.png)

* Select " Continue with limited setup" in the left bottom corner

![install7](Images/install7.png)

* Give a name and password to your local account
* Answer the three security questions
* Set all other options to the minimale value (no location, no track, etc.)

# CONFIGURATION OF WINDOWS
* Connect to your administrator account
* Go to "Open Network & Internet Setting"
* Change adapter options
* Select your card properties
* Go to "Internet Protocol Version 4" > Properties
* 
![setting01](Images/setting01.png)

* Give IP

![setting02](Images/setting2.png)

* Try to join the gateway (so your LAN INTERFACE in pfsense)

![setting3](Images/setting3.png)

* Rename the server with a easy name to remember/use.

![setting4](Images/setting4.png)
![setting5](Images/setting5.png)

* Restart your VM

# ADD YOUR WORKSTATION TO THE DOMAIN
* Go to "Advanced system setting"
* Select "Change"

![setting6](Images/setting6.png)

* Select "Domain" and give your netbios domain name
* Give your Administrator domain account credentials

![setting7](Images/setting7.png)

* Reboot your VM