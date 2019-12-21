# Introduction

The proposal of this documentation is to expose the necessity to create this project and why I chose all the config.

On this repository you can find all the documentation from installation to full config on my Raspberry Pi comand by comand. Most of the resources are external, because I preffer to give credit to the people how created the tutorial.

## Necessity 

I wanted to have a server to be able to **host websites, deploy websites, store files, have access to the servers cli and tunneling connections**. 

All this features must be available in **local network and internet**. Preferable using a **domainname** when I connect from internet.

One of the most important things for this project is to don't have to spend money on software or services. The unique cost of this project must be the **Raspberry Pi 3 B+, SD Card 64GB, electricity and internet connection 200 Mbps**.

# Raspbian Installation

The distro I use is [Raspbian Lite](https://www.raspberrypi.org/downloads/raspbian/) because I don't need any UI to interact with. And the software to burn the image 
into the SD is called [Rufus](https://rufus.ie/) because I am using a Windows as a main OS on current computer.

## Raspbian Configuration

If you want a exposed internet server you must conseider some important things depending of how paranoid you are with security, but for me these are fine:
- Configure a static IP in Raspberry and router to have the same access IP.
- Delete pi user and create you own one with robust password.
- Use a DMZ [(demilitarized zone)](https://en.wikipedia.org/wiki/DMZ_(computing)) to save you internal network if someone access to you server.
- Open the only necessary ports to access from the internet to you server.

## Current network configuration.

As I said in the last point, its important to have a DMZ wich normally is setting up a firewall (as in my case) to separe the two networks and don't be able to even ping from internal network. The next image ilustre my current network configuration (obviously without showing the real IP): 

![Network Diagram](./network_diagram.png)

## The opened and routed ports

I chose to open the less ports as it was possible, to do not be soo exposed on the internet. The ports are:

- 22 TCP port: to connect using SSH.
- 80 TCP/UDP port: to connect the web server.
- 9898 UDP: for the OpenVPN server.

*The current reason that I am not using HTTPS (443) is because the webs I want to host are not using any authentication or personal information to be needed to secure.

# Software 

- **SSH** to connect to Raspberry PI CLI. 
- **OpenVPN** to create a Virtual Private Network.
- **Apache 2** to host websites.

## SSH Configuration

SSH is already installed in Raspberry Pi you only have to activate it. This tutorial gives you the posibility to configure SSH command by command [SSH intro raspberry](https://itsfoss.com/ssh-into-raspberry/).

## OpenVPN Installation 

To install OpenVPN server I decided to follow the tutorial [How to setup and OpenVpn Server on a Raspberry Pi](https://dzone.com/articles/how-to-setup-an-openvpn-server-on-a-raspberry-pi). Which comes with a script to be executed in the Raspberry Pi and information for each screen.

## Apache 2 Installation

To install Apache 2 is really easy only execute the command:

```
sudo apt install apache2
```

Obviously in the future you will be needed some modules to be installed when the HTTPS or subdomains are used, but for now it works.
