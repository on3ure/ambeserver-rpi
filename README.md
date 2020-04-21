# AmbeServer node.js Raspberry PI Zero #

### Why ###
Looking for a solution i bumped on a NodeJS implementation. I liked the approach, code style and implementation.

d3dx9 [node-ambeserver](https://github.com/d3dx9/node-ambeserver)

### Install on Linux - Raspberry PI Zero ... Buster Release (2020) ###

## Install Dependancies ##
```console
sudo apt -y update
sudo apt -y full-upgrade
sudo apt -y install git conspy npm
```

## Install node-ambeserver ##
```console
cd ~
git clone https://github.com/d3dx9/node-ambeserver
cd node-ambeserver
npm install


## Install start scripts ##
```console
cd ~
git clone https://github.com/on3ure/ambeserver-rpi.git
cd ambeserver-rpi
sudo mkdir -p /ambeserver
sudo cp ambeserver.service /lib/systemd/system/
sudo cp -rf ~/node-ambeserver/* /ambeserver

sudo systemctl --system daemon-reload

sudo systemctl enable ambeserver
sudo systemctl start ambeserver
```

## Disable bluetooth ##
```console
echo "dtoverlay=pi3-disable-bt" | sudo tee -a /boot/config.txt
sudo systemctl disable hciuart
reboot
```

## Console ##
You can monitor the ambeserver on console tty3 via
```console
conspy 3
```
Press 3 times ESC to exit
