---
layout: page
title : config
subtitle: installation et configuration
---

# Rapsberry pi
### Procedure d'installation 'osx friendly'



* #### Installer un OS «frais» sur le Rasberry pi
	* Télécharger Raspbian jessie ou wheezy (debian based pi)
		* [raspbian sur le site officiel](http://www.raspberrypi.org/downloads/)
		* Décompresser le fichier zip pour obtenir un fichier .img
	* Tranferer l'image disque vers la carte SD
		* Simple avec GUI
		* [Apple Pi Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)
		* Voir instructions plus bas dans le lien ci-haut
		* Simple avec ligne de commande
		* https://www.raspberrypi.org/documentation/installation/installing-images/mac.md
		* Une fois l'operation terminée,  placer la carte sd ou micro sd dans le Pi et alimenter en 5v.



#### Trouver le Pi
* S'assurer que les deux ordinateurs soient sur le même réseau.
	* `ping raspberrypi.local`
	* Devrait retourner une ligne
	* ` 64 bytes from 192.168.0.107: icmp_seq=0 ttl=64 time=1.809 ms`
	* où `192.168.0.107` est l'adresse du Pi
*  Applications pour trouver le Pi
	*  à la manière «brute» [Angry ip Scanner](http://angryip.org)
	*  Plus élégant : [Adafruit pi finder](https://github.com/adafruit/Adafruit-Pi-Finder/releases/tag/v2.0.1-beta)
	*  Dans le cas d'un reseau filaire Ad-Hoc sur OSX,  le Pi devrait se trouver dans la zone 192.168.2.xxx  
	*  (mettre ici les info concernant le partage de sa connection et l'adresse sur 192.168.2.x)


* #### Accéder via SSH
	* ouvrir une fenêtre de terminal et taper :
	* `ssh pi@raspberrypi.local`
	* `ssh pi@192.168.111.251`
		* oû 192.168.111.251 doit être remplacer par l'adresse Ip du raspberry pi
		* le mot de passe : raspberry
		* l'utilisateur : pi

			* PS : S'assurer que sa fenêtre du terminal supporte les couleur ANSI (Préférence terminal)  
		* Dans l'éventualité que l'erreur suivante est rencontrée :
			 ```
			@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
			@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
			@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
				```
	* appliquer la commande suivante:
		* `ssh-keygen -R raspberrypi.local`
		* `ssh-keygen -R 192.168.XXX.YYY`
		* où XXX et YYY sont correspondent à l'adresse IP du PI que vous tentez d'Acceder.
