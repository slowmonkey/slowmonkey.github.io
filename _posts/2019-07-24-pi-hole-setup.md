---
layout: post
title: "Pi-hole Setup"
categories: [security, raspberrypi]
tags: [raspberrypi, pihole]
---
Pi-hole is network wide ad-blocking mechanism utilising a Raspberry Pi. It provides ad-blocking via a DHCP server and/or DNS Server.

# Table Of Contents <!-- omit in toc -->
- [Requirements](#requirements)
- [Installing an operating system onto the Raspberry Pi](#installing-an-operating-system-onto-the-raspberry-pi)
- [Enabling the Raspberry Pi for SSH connectivity](#enabling-the-raspberry-pi-for-ssh-connectivity)
- [Connect Raspberry Pi to the network](#connect-raspberry-pi-to-the-network)
- [Installing Pi-hole on the Raspberry Pi](#installing-pi-hole-on-the-raspberry-pi)
- [Testing the Pi-hole](#testing-the-pi-hole)
- [Configure devices on your network to use Pi-hole](#configure-devices-on-your-network-to-use-pi-hole)
- [Issues I have encountered](#issues-i-have-encountered)
  - [Nest Cams not connecting](#nest-cams-not-connecting)
  - [Pi-hole dashboard is unreachable](#pi-hole-dashboard-is-unreachable)

# Requirements
1. Raspberry Pi
2. Lan Cable (used to connect the Raspberry Pi to the router)
3. 8gb SD card for the Raspberry Pi
4. Power cable for the Raspberry Pi
5. SD Card reader

# Installing an operating system onto the Raspberry Pi

This step has vastly improved from when I first bought the device.

1. Go to [Raspberry Pi Downloads Section](https://www.raspberrypi.org/downloads/raspbian/)
2. Download the recommended operating system's zip file. At the time of writing I opted to install the recommended Raspbian OS.
3. Follow the steps in the link provided to write an image to the SD Card. [Installation Guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).

# Enabling the Raspberry Pi for SSH connectivity

1. Disconnect the SD Card and Reconnect it. You should now see 2 extra drives. A Boot Drive and a USB Drive.
2. Navigate to the Boot Drive.
3. On the root directory add an empy ssh directory

# Connect Raspberry Pi to the network

1. Install the SD card to the Raspberry Pi.
2. Connect the Raspberry Pi directly to the router via the LAN cable you purchased.
3. Plug the power cable in and wait.

# Installing Pi-hole on the Raspberry Pi

1. Log into your router.
2. Find the IP Address for the Raspberry Pi.
3. Reserve the IP Address for the Raspberry Pi via the MAC Address.
4. ssh into the Raspberry Pi using the following command:

    `ssh pi@<IP Address Here>`

5. The default password for the raspberry pi is: 
   
   `raspberry`

6. Change the password and store it somewhere safe. I recommend using a password manager.
7. Follow the installation instructions [here](https://github.com/pi-hole/pi-hole)
8. During the installation I just selected all the defaults.

# Testing the Pi-hole

Once the installation has completed:

1. Select a device connected to your home network and set the DNS of the device to the ip address for the Raspberry Pi.
2. Navigate to a web page with heavy ad usage.
3. Navigate to

    `http://<Raspberry PI - IP Address>/admin`

4. Observe the ads being blocked for the site you visited.

# Configure devices on your network to use Pi-hole

Follow the instructions [here](https://discourse.pi-hole.net/t/how-do-i-configure-my-devices-to-use-pi-hole-as-their-dns-server/245).

# Issues I have encountered

## Nest Cams not connecting

I have noticed that my nest cams have struggled to connect to the internet. It eventually fixed itself. I have however discovered several mitigations to solve this issue.

1. Re-enable the Router DHCP server until the nest cams are connected. The issue here I believe is when the IP Address lease expires I will encounter the same issue.
   
2. Add the nest cam devices to the dnsmasq list to exclude the devices from filtering. Follow the instructions by **deathbybandaid** [here](https://discourse.pi-hole.net/t/exclude-certain-lan-addresses-from-filtering/2014/13)

    Just incase the instructions are lost here is what was stated:

```
With the help of reddit, I managed to find a way to bypass the pihole straight to google 8.8.8.8 , It is set up by mac address.

Find the mac address and place this in your /etc/dnsmasq.d/ directory 273.

cd /etc/dnsmasq.d/

wget https://raw.githubusercontent.com/deathbybandaid/piadvanced/master/piholetweaks/dnsmasqtweaks/04-bypass.conf

nano 04-bypass.conf
(replace mac address)

dnsmasq --test
(tests the configuration)

sudo service dnsmasq restart
Or
sudo reboot

It would be awesome to do something like this via the webui!
```

## Pi-hole dashboard is unreachable

The correct way to combat this issue as pain-free as possible is to:
1. Re-enable the router's DHCP service.
2. ssh into the raspberry pi and restart it.

**NOTE**

If you just power-cycle the Raspberry Pi it may have trouble re-connecting to the router as I discovered. You will have to either directly connect a device via a LAN cable to the router or use a device that still has a valid IP address leased to it to perform the above steps.
