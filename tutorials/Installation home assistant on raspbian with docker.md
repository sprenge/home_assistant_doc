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

The tool will write the image file to the SD card and verify it.  It is important that this step does not fail !

![image-20200303094025179](image-20200303094025179.png)



## Step 3. Prepare the SD card for wifi connectivity / ssh access

Reinsert the SD card in your laptop/PC, Open MobaXterm and start a local terminal

![image-20200303094447463](image-20200303094447463.png)

Execute the follow commands in the terminal :

```
cd /cygdrive/d
touch ssh
touch wpa_supplicant.conf
edit wpa_supplicant.conf
```

Forsee the following text in the wpa_supplicant.conf file :

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```

Lookup your country code in https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes

Fill in NETWORK-NAME and NETWORK-PASSWORD