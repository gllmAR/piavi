---
layout: page
title : Jessy
subtitle: Raspbian Jessy
---

#### enlever paquet lourd et vraiment long à updater

```
sudo apt-get remove nuscratch scratch libreoffice libreoffice-gtk claws-mail minecraft-pi penguinspuzzle python-minecraftpi python3-minecraftpi
```

`sudo apt-get autoremove`


#### Mise à jour des paquets
* `sudo apt-get update `
* `sudo apt-get upgrade `
* ou les deux commandes à la suite de l'autre : `sudo apt-get update && sudo apt-get upgrade`


#### Configurer le Pi via raspi-config
[info sur raspi-config](http://elinux.org/RPi_raspi-config)

*  exécuter dans un terminal : `sudo raspi-config`
	* Expand the root partition to fill the disk
	* Choisir son mode de boot (command line ou autologin)
		* Start desktop on boot
	* Change the hostname
		* Pour reconnaitre le pi sur le réseau
	* Change the default password
		* bonne pratique...
* `sudo reboot`


####  Activer NetTalk (être vu sur le réseau),  filesharing AFP et VNC OSX compatible sur le pi

##### compilé depuis les sources suivantes :
* vnc :   [ http://dennistt.net/2013/09/15/raspberry-pi/](http://dennistt.net/2013/09/15/raspberry-pi/)
* infos [netatalk](http://www.raspberrypi.org/forums/viewtopic.php?f=36&t=26826)
* file sharing : [http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html](http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html)

##### installer les dépendances requises (netatalk et x11vnc)
* `sudo apt-get install netatalk x11vnc`

##### Activer et configurer le file sharing AFP (apple file protocol)
* `sudo nano /etc/avahi/services/afpd.service`

##### coller le texte suivant

```
<?xml version="1.0" standalone='no'?> <!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   	<name replace-wildcards="yes">%h</name>
   	<service>
      <type>_afpovertcp._tcp</type>
      	<port>548</port>
   	</service>
</service-group>
```


##### redémarrer le serveur avahi
* `sudo /etc/init.d/avahi-daemon restart`

##### Activer et configurer le VNC au démarage
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

##### Régler les permissions (afin de pouvoir exécuter) le fichiers créé
* `sudo chmod +x ~/.config/autostart/x11vnc.desktop`

##### Configurer le service AVAHI (avertir le pi sur le réseau)
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


* forcer le HDMI
	* http://pi.eggum.net/2013/06/force-hdmi-out.html


#### désactiver le screen blanking
éditer le fichier suivant et rajouter les commandes après la première ligne
* ` sudo nano /etc/X11/xinit/xinitrc  `

```
xset s off         # don't activate screensaver
xset -dpms         # disable DPMS (Energy Star) features.
xset s noblank     # don't blank the video device
```









----

#### à investiguer d'avantage

* mesh networking wireless [http://www.netlore.co.uk/airmesh/?page=about](http://www.netlore.co.uk/airmesh/?page=about)

* sampler qui boot en 8 secondes!
[http://www.samplerbox.org](http://www.samplerbox.org)

* nodeJs
	* source [https://learn.adafruit.com/node-embedded-development/installing-node-dot-js](https://learn.adafruit.com/node-embedded-development/installing-node-dot-js)


* Openframeworks
	* [https://github.com/openframeworks/openFrameworks](https://github.com/openframeworks/openFrameworks)

	* [https://github.com/openFrameworks-arm/Resonate2013Workshop]([https://github.com/openFrameworks-arm/Resonate2013Workshop)
	* [http://forum.openframeworks.cc/t/raspberry-pi-2-setup-guide/18690](http://forum.openframeworks.cc/t/raspberry-pi-2-setup-guide/18690)
	* export MAKEFLAGS=-j4 PLATFORM_VARIANT=rpi2



* Synergy :
	* synergy est un utilitaire qui permet d utiliser le clavier et la souris d un ordinateur directement vers un ordinateur distant
	Sur le Pi
	* sudo apt-get install synergy
	``` synergyc --name pi 192.168.111.100 ```
	* sur l'ordinateur serveur
	* Installer ou compiller synergy
mettre en auto stard

https://learn.adafruit.com/synergy-on-raspberry-pi/setup-synergy-client-autostart
