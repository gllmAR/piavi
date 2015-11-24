---
layout: page
title : PIAVI
subtitle: PI AudioVisuel Interactif
---
### Abstract

Assembler un environnement de lecture et de génération audiovisuel interactif à la fois autonome et asservissable.

Créer différents modules répondant aux besoins d'aquisitions, de traitement et de diffusions des données.

Chaque module communique par un protocol standardisé (OSC - open sound control) rendant le déploiment modulaire.


En X composantes

  - Service GPIO (protocol  OSC)
  - Module de lecture et de sythèse sonore  (pure data vanilla?)
  - Module de lecture vidéo  (omx player osc wrapper?)
  - Module de génération visuel (openframework?)
  - Exposer les paramètres modifiable via une interface web
  - Webserver permetant le controle de paramètre (node.js, socket.io et OSC)
  -
Communique bidirectionnellement avec des paramètres interne via le protocol OSC.  

### Installation
git clone --recursive

Pour le pi :
suivre d'abord ce guide
[https://learn.adafruit.com/node-embedded-development/installing-node-dot-js](https://learn.adafruit.com/node-embedded-development/installing-node-dot-js)
### liens

aide à configurer

[https://github.com/adafruit/Adafruit-Pi-Finder](https://github.com/adafruit/Adafruit-Pi-Finder)


à implémenter :

[https://learn.adafruit.com/raspberry-pi-open-sound-control/interacting-with-a-web-browser](https://learn.adafruit.com/raspberry-pi-open-sound-control/interacting-with-a-web-browser)

à fouiller :

[https://github.com/russellmcc/node-osc-min](https://github.com/russellmcc/node-osc-min)



OSC et GPIO :

[http://www.instructables.com/id/Raspberry-Pi-GPIO-home-automation/step6/Install-App/](http://www.instructables.com/id/Raspberry-Pi-GPIO-home-automation/step6/Install-App/)

[https://github.com/misterhay/RasCough/blob/master/RasCough.py](https://github.com/misterhay/RasCough/blob/master/RasCough.py)

[https://github.com/soundmaking/RPi8pinIO](https://github.com/soundmaking/RPi8pinIO)


audio :

[https://github.com/yomguy/PiPlayer](https://github.com/yomguy/PiPlayer)

[https://github.com/jacoscaz/osc-browser-synth](https://github.com/jacoscaz/osc-browser-synth)

Vidéo :


Interface :

[https://github.com/lsu-emdm/nexusUI](https://github.com/lsu-emdm/nexusUI)

[http://reactivemusic.net/?tag=osc](http://reactivemusic.net/?tag=osc)

Un projet qui regroupe beaucoup des fonctionnalité
[http://pocketvj.com](http://pocketvj.com)

Video player OSC  (openframework et omxplayer)
[https://github.com/Hemisphere-Project/HPlayer](https://github.com/Hemisphere-Project/HPlayer)

basé sur :
[https://github.com/jvcleave/ofxOMXPlayer](https://github.com/jvcleave/ofxOMXPlayer)


Investiguer Node-Red



investiguer gstreamer

[https://wiki.matthiasbock.net/index.php/Hardware-accelerated_video_playback_on_the_Raspberry_Pi](https://wiki.matthiasbock.net/index.php/Hardware-accelerated_video_playback_on_the_Raspberry_Pi)

[http://www.onepitwopi.com/raspberry-pi/gstreamer-1-2-on-the-raspberry-pi/](http://www.onepitwopi.com/raspberry-pi/gstreamer-1-2-on-the-raspberry-pi/)

http://blog.pi3g.com/2013/08/ffmpeg-gstreamer-raspberry-pi-windows-desktop-streaming/

[http://rpiquadcopter.blogspot.fi/2014/06/raspberry-pi-camera-module-video.html](http://rpiquadcopter.blogspot.fi/2014/06/raspberry-pi-camera-module-video.html)

[https://github.com/avilleret/rpi_osc_video_player](https://github.com/avilleret/rpi_osc_video_player)

investiguer DBUS

http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html
