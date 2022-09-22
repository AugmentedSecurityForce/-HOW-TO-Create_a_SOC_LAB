- [ACCOUNT](#account)
- [INSTALL FOR LINUX](#install-for-linux)
- [INSTALL FOR WINDOWS](#install-for-windows)
- [ADVANCED INSTALL FOR WINDOWS](#advanced-install-for-windows)
# ACCOUNT
* Go to the [crowdsec site](https://www.crowdsec.net/)
* Select "create free account"
* Create the free account and log in to CrowdSec.

# INSTALL FOR LINUX
* When you're log in you have all informations to install it on linux.

![crowdsec01](crowdsec01.png)

# INSTALL FOR WINDOWS
* Go to the [GitHub page](https://github.com/crowdsecurity/crowdsec/releases/latest)
* Download the msi file on the Windows computer (server and workstation)
* Launch it

![install01](Images/install01.png)
![install02](Images/install02.png)
![install03](Images/install03.png)

* Waiting

![install04](Images/install04.png)
![install05](Images/install05.png)


Contrary to Linux, CrowdSec does not yet support the automatic configuration at installation time. If you want to be able to detect something other than RDP or SMB bruteforce, then you will need to customize your acquisition configuration.

* Launch Powershell with administrator in CrodwSec's folder
* .\cscli collections install crowdsecurity/windows-firewall

![install06](Images/install06.png)

* Open the acquis.yaml file in "C:\ProgramData\CrowdSec\config\"
* Add this to it : 
![install07](Images/install07.png)

* Reboot the computer

# ADVANCED INSTALL FOR WINDOWS
If you want your Crowdsec can block you have to install the Windows Firewall Bouncer Installation.
* Go to the [dedicated page](https://github.com/crowdsecurity/cs-windows-firewall-bouncer/releases)
* Download the bundle file (contain all dependancies)
* Launch it

![install08](Images/install08.png)

* Waiting

![install09](Images/install09.png)
![install10](Images/install10.png)
![install11](Images/install11.png)
![install12](Images/install12.png)
![install13](Images/install13.png)
![install14](Images/install14.png)

* Waiting

![install15](Images/install15.png)
![install16](Images/install16.png)