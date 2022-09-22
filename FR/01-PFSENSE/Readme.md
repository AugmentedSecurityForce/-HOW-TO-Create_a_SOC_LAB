- [TELECHARGEMENT](#telechargement)
- [CONFIGURATION DE VIRTUALBOX](#configuration-de-virtualbox)
- [INSTALLATION](#installation)
- [CONFIGURATION](#configuration)

# TELECHARGEMENT
* Se rendre sur le [site officiel](https://www.pfsense.org/download/)
* Télécharger la dernière version stable, community edition

# CONFIGURATION DE VIRTUALBOX
* Créer une nouvelle VM

![setting01](Images/setting01.png)
![setting02](Images/setting02.png)
![setting03](Images/setting03.png)
![setting04](Images/setting04.png)
![setting05](Images/setting05.png)
![setting06](Images/setting06.png)

* Aller dans les propriétés de la VM
* Dans la partie réseau, activer les trois adaptateurs
  * Noter les adresses MAC sur un papier, ça servira plus tard.

Configuration de la zone rouge (réseau externe, hors entreprise)
![setting07](Images/setting07.png)

Configuration de la zone verte (réseau interne à l'entreprise)
![setting08](Images/setting08.png)

Configuration de la zone oranfz (DMZ)
![setting09](Images/setting09.png)

* Démarrer la VM
  * Monter l'ISO télécharger précédemment.

![setting10](Images/setting10.png)

# INSTALLATION
* Accepter la licence
* 
![install01](Images/install01.png)

* Sélectionner "install"
  
![install02](Images/install02.png)

* Sélectionner votre clavier
* Laisser le partitionnement par défaut (on est dans un lab)
* Lancer l'installation (pas de raid ni chiffrement, rien)
* Patienter

![install03](Images/install03.png)

* Ne lancer pas la configuration manuelle
* 
![install04](Images/install04.png)

* Redémarrer la VM

# CONFIGURATION

![conf01](Images/conf01.png)

* Sélectionner 1 pour configurer les interfaces

![conf02](Images/conf02.png)

_Voici pourquoi il fallait noter les adresses MAC_.

* Sélectionner la carte avec la mac de la zone rouge pour la zone WAN
* Sélectionner la carte avec la mac de la zone verte pour la zone LAN
* Sélectionner la carte avec la mac de la zone orange pour la zone DMZ

![conf03](Images/conf03.png)

* Confirmer

![conf04](Images/conf04.png)

* Sélectionner 2 pour configurer les adresses IP
* Laisser l'interface WAN en DHCP
* Sélectionner 2 pour configurer l'interface LAN
* Configurer l'IP et le sous-réseau voulu (voir schéma précédent)

**Mettre "non" pour la passerelle**