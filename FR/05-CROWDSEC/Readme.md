- [ACCOUNT](#account)
- [INSTALL FOR LINUX](#install-for-linux)
- 
- 
- # COMPTE
* Se rendre sur le site de [crowdsec site](https://www.crowdsec.net/)
* Créer un compte
* Se connecter

# INSTALLATION POUR LINUX
* Une fois connecté, vous avez toutes les informations pour l'installer sur votre distribution Linux préférée.

![crowdsec01](crowdsec01.png)

# INSTALLATION POUR WINDOWS
* Se rendre sur la [page GitHub](https://github.com/crowdsecurity/crowdsec/releases/latest)
* Télécharger le fichier .msi sur votre VM
* Exécuter le.

![install01](Images/install01.png)
![install02](Images/install02.png)
![install03](Images/install03.png)

* Patienter

![install04](Images/install04.png)
![install05](Images/install05.png)


Contrairement à la version Linux, CrowdSec Windows ne supporte pas encore la configuration automatique au moment de l'installation. Si vous voulez être capable de détecter autre chose que le bruteforce RDP ou SMB, alors vous devrez personnaliser votre configuration d'acquisition.

* Exécuter Powershell en administrateur depuis le dossier CrowdSec
* .\cscli collections install crowdsecurity/windows-firewall

![install06](Images/install06.png)

* Editer le fichier "acquis.yaml" dans "C:\ProgramData\CrowdSec\config\"
* Ajouter ceci : 
![install07](Images/install07.png)

* Redémarrer le poste

# ADVANCED INSTALL FOR WINDOWS
Si vous voulez que CrowdSec ajoute automatiquement les règles de blocage à votre parefeu local il faut installer ""Windows Firewall Bouncer".
* Se rendre sur la [page dédiée](https://github.com/crowdsecurity/cs-windows-firewall-bouncer/releases)
* Télécharger le fichier bundle (contient tous les prérequis)
* Exécuter le.

![install08](Images/install08.png)

* Patienter

![install09](Images/install09.png)
![install10](Images/install10.png)
![install11](Images/install11.png)
![install12](Images/install12.png)
![install13](Images/install13.png)
![install14](Images/install14.png)

* Patienter

![install15](Images/install15.png)
![install16](Images/install16.png)

* Redémarrer