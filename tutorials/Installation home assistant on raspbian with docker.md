# Installation home assistant on raspbian with docker

The assumption is that the installation is done from PC/laptop without windows installed.

## Step 1 : hardware preparation steps

Download raspbian lite (not desktop) via https://www.raspberrypi.org/downloads/raspbian/ and unzip the image file (something like 2020-02-13-raspbian-buster-lite.img).  Store the image file somewhere in a folder.

Install the following (free) packages on your pc or laptop :

- MobaXterm (home edition) : https://mobaxterm.mobatek.net/download.html
- Balena Etcher : https://www.balena.io/etcher/

A rasberry pi device needs a micro SD card (32GB is adviced).  Put the card in an adapter in plugin it in your laptop/pc.  I assume that the card is discovered as D: drive (can be a different letter in your case, please replace D: by what you discover on your laptop/PC).  I am using a rasberry pi 3 model B. 

## Step 2 : Burn the raspbian image to the micro SD card

Insert the SD card in your computer and open the Balena Etcher application, select the above mentioned image file, select the SD card (in my case the D: driver) and press the flash button

![image-20200303094025179](C:\Users\sprengee\AppData\Roaming\Typora\typora-user-images\image-20200303094025179.png)

The tool will write the image file to the SD card and verify it.  It is important that this step does not fail !

## Step 3. Prepare the SD card for wifi connectivity / ssh access

Reinsert the SD card in your laptop/PC, Open MobaXterm and start a local terminal

![image-20200303094502340](C:\Users\sprengee\AppData\Roaming\Typora\typora-user-images\image-20200303094502340.png)