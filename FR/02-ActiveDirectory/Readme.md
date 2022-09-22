- [TELECHARGEMENT](#telechargement)
- [CONFIGURATION DE VIRTUALBOX](#configuration-de-virtualbox)
- [INSTALLATION DE WINDOWS](#installation-de-windows)
- [CONFIGURATION DE WINDOWS](#configuration-de-windows)
- [INSTALLATION D'ACTIVE DIRECTORY](#installation-dactive-directory)
- [CONFIGURATION DE ACTIVE DIRECTORY](#configuration-de-active-directory)

# TELECHARGEMENT
* Se rendre sur le [Microsoft evalcenter](https://www.microsoft.com/fr-fr/evalcenter/evaluate-windows-server-2022)
* Télécharger le fichier ISO
  * Vous pouvez mettre de fausses informations.
  * 
![download1](Images/download1.png)

* Télécharger l'ISO in "64 bits English"

# CONFIGURATION DE VIRTUALBOX
* Créer une nouvelle VM

![vm01](Images/vm1.png)
![vm02](Images/vm2.png)
![vm03](Images/vm3.png)
![vm04](Images/vm4.png)
![vm05](Images/vm5.png)
![vm6](Images/vm6.png)

* Se rendre dans les propriétés de la VM
* Configurer la carte réseau en réseau interne : GREEN

![vm7](Images/vm7.png)

* Démarrer la VM
  * Monter l'ISO Windows Server télécharger précédemment.

# INSTALLATION DE WINDOWS
* Installer en anglais-US.
  * Le reste peut être configurer comme vous voulez, mais toujours installer vos OS en anglais !

![install01](Images/install01.png)

* Sélectionner "install now"
* Sélectionner "Windows Server 2022 Datacenter Evaluation (Desktop Experience)".
  * On est dans un lab, aucun jugement a installer la GUI.

![install02](Images/install02.png)

* Accepter la licence
* Sélectionner Custom install

![install03](Images/install03.png)

* Sélectionner votre seul disque

![install04](Images/install04.png)

* Patienter durant l'installation et le redémarrage
* Configurer votre mot de passe (vous êtes dans un lab, Bonjour01 est valide ;) )

# CONFIGURATION DE WINDOWS
* Se connecter en administrator
* Vous rendre dans "Open Network & Internet Setting"

![ad1](Images/AD1.png)

* Changer la configuration de l'adaptateur

![ad2](Images/AD2.png)

* Sélectionner les propriétés de la carte
* Se rendre sur "Internet Protocol Version 4" > Properties

![ad3](Images/AD3.png)

* Configurer l'IP

![ad4](Images/AD4.png)

* Pinger votre passerelle (IP de LAN INTERFACE sur pfsense)

![ad5](Images/AD5.png)

* Renommer le serveur .

![ad6](Images/AD6.png)
![ad7](Images/AD7.png)

* Redémarrer la VM

# INSTALLATION D'ACTIVE DIRECTORY
* Se connecter en administrator
* Sélectionner "Add roles and features"

![ad8](Images/AD8.png)

* Sélectionner  role-based installation
* Sélectionner le seul serveur listé
* Sélectionner "Active Directory Domain Services"

![ad9](Images/AD9.png)
![ad10](Images/AD10.png)

* Laisser la configuration par défaut
* une fois l'installation finie, sélectionner "promote this server to a domain controller"

![ad11](Images/AD11.png)

* Ajouter une nouvelle foret
* 
![ad12](Images/AD112.png)

* Laisser la configuration par défaut et configurer un mot de passe simple (encore une fois, on est dans un lab)

![ad13](Images/AD113.png)

* Laisser la configuration DNS par défaut
* Noter la partie "netbios domain name", il s'agit de ce qu'il faudra mettre avant le \ lors des connexions au domaine.
* Laisser les dossiers par défaut
* Lancer l'installation
* Redémarrer quand demandé

# CONFIGURATION DE ACTIVE DIRECTORY
Maintenant, il faut remplir votre AD avec des données, failles, etc. 
Pour le faire facielement, on va utiliser [BadBloud](https://github.com/davidprowe/BadBlood)

* Télécharger le sur votre AD
* Décompresser le fichier
* Exécuter Powershell en administrateur
* Naviguer jusqu'au dossier Badblood
* Exécuter Invoke-BadBlood.ps1
* Laisser la magie opérer !

![badblood1](Images/badblound1.png)
![badblood2](Images/badblound2.png)