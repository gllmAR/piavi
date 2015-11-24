---
layout: page
title : wheezy
subtitle: rasbian Wheezy
---

# Rapsberry pi
### Procedure d'installation 'osx friendly'


* #### Installer un OS «frais» sur le Rasberry pi
	* Télécharger Raspbian  (debian based pi)
		* [raspbian sur le site officiel](http://www.raspberrypi.org/downloads/)
		* Décompresser le fichier zip pour obtenir un fichier .img
	* Tranferer l'image disque vers la carte SD
		* Simple avec GUI
		* [Apple Pi Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)
		* Voir instructions plus bas dans le lien ci-haut
		* Simple avec ligne de commande
		* https://www.raspberrypi.org/documentation/installation/installing-images/mac.md
		* Une fois l'operation terminée,  placer la carte sd ou micro sd dans le Pi et alimenter en 5v.

* #### Trouver le Pi
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
    		*  

* #### Accéder via SSH
	* ouvrir une fenêtre de terminal et taper :
		* `ssh pi@raspberrypi.local`
		* `ssh pi@192.168.111.251`
			* oû 192.168.111.251 doit être remplacer par l'adresse Ip du raspberry pi
			*
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
				où XXX et YYY sont correspondent à l'adresse IP du PI que vous tentez d'Acceder.


* #### Mise à jours et configuration sommaire
	* `sudo apt-get update `
	* `sudo apt-get upgrade `
	* ou les deux commandes à la suite de l'autre : `sudo apt-get update && sudo apt-get upgrade`

	* 	Configurer le Pi (changer le mot de passe,  le nom du pi et booter en desktop?)
		* `sudo raspi-config`
			* Expand the root partition to fill the disk
			* Choisir son mode de boot (command line ou autologin)
				* Start desktop on boot
			* Change the hostname
				* Pour reconnaitre le pi sur le reseau
			* Change the default password
				* bonne pratique...
		* `sudo reboot`


*  [info sur le raspi-config](http://elinux.org/RPi_raspi-config)




* ####  Activer NetTalk (être vu sur le réseau),  filesharing et VNC sur le pi
	* vnc :   [ http://dennistt.net/2013/09/15/raspberry-pi/](http://dennistt.net/2013/09/15/raspberry-pi/)
	* infos [netatalk](http://www.raspberrypi.org/forums/viewtopic.php?f=36&t=26826)
	* file sharing : [http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html](http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html)

	* installer les dépendances requises (netatalk et x11vnc)
		* `sudo apt-get install netatalk x11vnc`

	* Activer et configurer le file sharing AFP (apple file protocol)

		* `sudo nano /etc/avahi/services/afpd.service`
		```  
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   	<name replace-wildcards="yes">%h</name>
   	<service>
      <type>_afpovertcp._tcp</type>
      	<port>548</port>
   	</service>
</service-group>
```
		* `sudo /etc/init.d/avahi-daemon restart`

* Activer et configurer le VNC au démarage

	* Configurer le mot de passe (suivre les instructions à l'écran)
		* `x11vnc -storepasswd`

	* Configurer un raccourci pour démarrer automatiquement une commande.  
   	* `mkdir ~/.config/`
		* `mkdir ~/.config/autostart/`
   	* `nano ~/.config/autostart/x11vnc.desktop`

		* Y inscrire ce bloque de texte
		```
[Desktop Entry]
  Encoding=UTF-8
  Type=Application
  Name=X11VNC
  Comment=
  Exec=x11vnc -forever -usepw -display :0 -ultrafilexfer
  StartupNotify=false
  Terminal=false
  Hidden=false
	```

	* pour quitter nano,  ^x  (touche control+x  y enter)  

	* Régler les permissions (afin de pouvoir executer) le fichiers créé
   * `sudo chmod +x ~/.config/autostart/x11vnc.desktop`

  * Configurer le service AVAHI (avertir le pi sur le réseau)
	* `sudo nano /etc/avahi/services/rfb.service`
	* Coller ce bloque de texte
	```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
	<name replace-wildcards="yes">%h</name>
	<service>
		<type>_rfb._tcp</type>
		<port>5900</port>
	</service>
</service-group>
	```


	* sauvegarder  et quitter (ctrl+x)

* Redémarer le pi pour que cela prenne effet
	* `sudo reboot`


* forcer le hdmi
	* http://pi.eggum.net/2013/06/force-hdmi-out.html

* nodeJs
	* source [https://learn.adafruit.com/node-embedded-development/installing-node-dot-js](https://learn.adafruit.com/node-embedded-development/installing-node-dot-js)


* Openframeworks
	* [https://github.com/openframeworks/openFrameworks](https://github.com/openframeworks/openFrameworks)

	* [https://github.com/openFrameworks-arm/Resonate2013Workshop]([https://github.com/openFrameworks-arm/Resonate2013Workshop)
	* [http://forum.openframeworks.cc/t/raspberry-pi-2-setup-guide/18690](http://forum.openframeworks.cc/t/raspberry-pi-2-setup-guide/18690)
	* export MAKEFLAGS=-j4 PLATFORM_VARIANT=rpi2


* désactiver le screen blanking
	*  editer le fichier suivant et rajouter les commande apres la premierre ligne
	* ``` sudo nano /etc/X11/xinit/xinitrc ```
	* ```
xset s off         # don't activate screensaver
xset -dpms         # disable DPMS (Energy Star) features.
xset s noblank     # don't blank the video device
 ```
 *


* Synergy :
	* synergy est un utilitaire qui permet d utiliser le clavier et la souris d un ordinateur directement vers un ordinateur distant
	Sur le Pi
	* sudo apt-get install synergy
	``` synergyc --name pi 192.168.111.100 ```
	* sur l<ordinateur serveur
	* Installer ou compiller synergy
mettre en auto stard

https://learn.adafruit.com/synergy-on-raspberry-pi/setup-synergy-client-autostart

To remove stuff

sudo apt-get remove nuscratch scratch libreoffice libreoffice-gtk claws-mail minecraft-pi penguinspuzzle python-minecraftpi python3-minecraftpi

sudo apt-get autoremove




----

#### à investiguer d'avantage

* mesh networking wireless [http://www.netlore.co.uk/airmesh/?page=about](http://www.netlore.co.uk/airmesh/?page=about)

* sampler qui boot en 8 secondes!
[http://www.samplerbox.org](http://www.samplerbox.org)
