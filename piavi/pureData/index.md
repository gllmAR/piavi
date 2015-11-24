---
layout: page
title : pureData
subtitle: pureData et Raspberry-Pi
---

# PureData

### installation

#### pure data vanilla

télécharger l'executable à partir du site de Miller Puckette:



[http://msp.ucsd.edu/software.html](http://msp.ucsd.edu/software.html)

Pour le raspberry pi 1 (B, B+ A+)  : Pd version 0.46-7
 compiled for Raspberry Pi

Pour le Raspberry pi 2 : Pd version 0.46-7 compiled for UDOO


décompresser
executer le fichier binaire présent dans /bin/pd


#### compiler pd vanilla
Afin d'utiliser Jack avec pd,  il faut le compiler de la source

télécharger la source : Pd version 0.46-7 source

sudo apt-get install libasound2-dev automake autoconf libtool

mkdir ~/src && cd ~/src
wget http://msp.ucsd.edu/Software/pd-0.46-7.src.tar.gz
tar -zxvf pd-0.46-7.src.tar.gz
cd pd-0.46-7
./autogen.sh
./configure --enable-jack
make


Head : Est un lecteur Head(less) de patch PureData qui gère la communication OSC
et hardware vers des patchs chargé dans l'objet pd~ ()



Les bases pour réaliser un mixer OSC-MIXeR

Features :
OSC in

scaler les données entrantes
Déclencher des événements sur le concept de threhhold
sauvegarder un preset de paramètre
pouvoir loader un preset


OSC out


sources :

https://github.com/alexandros301/map/tree/master


à investiguer

https://github.com/m---w/kollabs
https://github.com/danomatika/BangYourHead
