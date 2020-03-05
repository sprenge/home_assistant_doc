# Installation home assistant on raspbian with docker (raspberry PI)

The assumption is that the installation is done from PC/laptop with windows (10) installed.

> Note : This tutorial assumes that you connect your raspberry PI with a fixed ethernet cable to your home network.  Wifi connections will be tackled in later tutorials.

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

> Note : Balena Etcher sometimes fails (sumcheck error):  See following [link](https://superuser.com/questions/1199823/how-to-prevent-creation-of-system-volume-information-folder-in-windows-10-for/1199824#1199824) how to avoid this.
>

## Step 3. Prepare the SD card for ssh access

Reinsert the SD card in your laptop/PC, Open MobaXterm and start a local terminal

![image-20200303094447463](image-20200303094447463.png)

Execute the follow commands in the terminal :

```
cd /cygdrive/d
touch ssh
```



## Step 4.  Power up the rasberry PI

Insert the micro SD card in the rasberry PI, connect the device using a fixed ether cable to your home router and give the device some power.  Wait now a couple of minutes, take a coffee.

## Step 5. SSH to the rasberry pi with your mobaxterm application

Go to the local terminal and enter following command (The default password is **raspberry**).

```
ssh pi@192.168.1.21
# or
ssh pi@raspberrypi.local
```

The IP can be looked with for instance the android app called fing.  This app will find the IP address of the raspberry PI if your phone is connected to the same home network.  Alternatively and if you are lucky (your router supports MDNS), you can use the hostname instead of the IP address.

```
sudo raspi-config
```

You will see a menu, change the following items :

- Under number 1, change the password to a safe one
- Under number 4, change language and regional settings
- Under number 7, advanced options, Execute A1 and finished (reboot if asked for)



## Step 6.  Install some prerequisite software on your PI

Ssh again into the device and enter the commands below :



Copy/paste following text in your ssh session

```
sudo apt update && sudo apt dist-upgrade -y && sudo apt autoremove
sudo -i
apt-get install software-properties-common
apt-get update
apt-get install -y apparmor-utils apt-transport-https avahi-daemon ca-certificates curl dbus jq network-manager socat
curl -fsSL get.docker.com | sh
```

```
curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh" | bash -s -- -m raspberrypi3
```

```
sudo docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
sudo reboot
```

Fire up now a browser and enter the IP address of the your PI on port 8123 (e.g. http://192.168.1.21:8123)

Once the installation is completed, create an account in home asisstant.