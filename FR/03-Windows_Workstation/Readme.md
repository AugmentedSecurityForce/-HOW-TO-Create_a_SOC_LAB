- [TELECHARGEMENT](#telechargement)
- [CONFIGURATION DE VIRTUALBOX](#configuration-de-virtualbox)
- [INSTALLATION OF WINDOWS](#installation-of-windows)
- [CONFIGURATION DE WINDOWS](#configuration-de-windows)
- [JOINDRE LA VM AU DOMAINE](#joindre-la-vm-au-domaine)

# TELECHARGEMENT
* Télécharger l'[outil fournit par Microsoft](https://go.microsoft.com/fwlink/?LinkId=691209)
* Exécuter le
* Accepte la licence d'utilisation
* Sélectionner "create a installation support" to make an ISO
* Sélectionner la langue anglaise

![download1](Images/download1.png)

* Sélectionner "ISO file"
* Enregistrer le fichier sur votre poste

# CONFIGURATION DE VIRTUALBOX
* Créer une nouvelle VM

![vm01](Images/vm1.png)
![vm02](Images/vm2.png)
![vm03](Images/vm3.png)
![vm04](Images/vm4.png)
![vm05](Images/vm5.png)
![vm6](Images/vm6.png)

* Se rendre dans les propriétés de la VM
* Configurer l'adaptateur réseau en internal network : GREEN

![vm7](Images/vm7.png)

* Démarrer la VM
  * Monter l'ISO précédemment créé.

# INSTALLATION OF WINDOWS
* Installer en anglais-US.
  * Le reste peut être configurer comme vous voulez, mais toujours installer vos OS en anglais !

![install1](Images/install1.png)

* Sélectionner "install now"
* Sélectionner "i don't have a product key" (or enter the one you have)

![install2](Images/install2.png)

* Sélectionner Windows 10 Pro version

![install3](Images/install3.png)

* Accepter la licence
* Sélectionner custom install

![install4](Images/install4.png)

* Sélectionner le disque dur pour installation

![install5](Images/install5.png)

* Patienter durant l'installation et le redémarrage
* Sélectionner votre région
* Sélectionner votre clavier
* Sélectionner "I don't have internet" en bas à gauche

![install6](Images/install6.png)

* Sélectionner " Continue with limited setup" en bas à gauche

![install7](Images/install7.png)

* Donner un nom et un mot de passe à votre compte local
* Répondre aux trois questions de sécurité
* Faite la configuration minimale (pas de géolocalisation, pas d'espionnage, etc.)

# CONFIGURATION DE WINDOWS
* Connectez-vous
* Se rendre dans "Open Network & Internet Setting"
* Changer la configuration de l'adaptateur
* Se rendre dans "Internet Protocol Version 4" > Properties
* 
![setting01](Images/setting01.png)

* Configurer l'IP

![setting02](Images/setting2.png)

* Pinger votre passerelle (l'IP de LAN INTERFACE dans pfsense)

![setting3](Images/setting3.png)

* Renommer votre machine.

![setting4](Images/setting4.png)
![setting5](Images/setting5.png)

* Redémarrer la VM

# JOINDRE LA VM AU DOMAINE
* Se rendre dans "Advanced system setting"
* Sélectionner "Change"

![setting6](Images/setting6.png)

* Sélectionner "Domain" et configurer le nom netbios
* Renseigner le compte Administrator de votre AD

![setting7](Images/setting7.png)

* Redémarrer