---
title: qos marking reference
tags: OpenGear
---

# Introduction
If anyone uses OpenGear console servers for out of band (OOB) serial console access over cellular networks, you’ve no doubt encountered the same relatively minor challenges I have:

1. You need a public IP address on the cellular modem so you can connect inbound
2. You need/want a central point of access so you don’t have to deal with dynamic DNS, or expose management services to the internet

After much tinkering, I’ve come up with a relatively simple and inexpensive way to solve these problems that doesn’t involving paying for OpenGear’s Lighthouse central management software, which is a bit overpriced in my view.

## Solution Summary
* Stand up out of band Linux server running OpenSSH.
* Configure OpenGear serial ports to allow direct access via SSH. This will, by default, expose ports 3001-30xx depending on your port density. If you SSH to these ports it will put you directly at the console of the connected device. For example, `ssh -p 3004 user@opengear` would SSH to the OpenGear on port 3004, and once the session is authenticated, you would be connected directly to the device on the OpenGear’s serial port 4.
* Configure OpenGear NET1/NET2 ports with access to your OOB LAN.
* Configure OpenGear Call Home feature to enable reverse SSH tunneling of all SSH:Serial port mappings to real ports on the OOB server.
    * OpenGear automatically SSHs to Linux Server
    * OpenGear reverse forwards Serial Port SSH ports, I.e. 3001 maps to 5001, 3002 maps to 5002, etc.
* Bonus: ports can be mapped to hosts reachable on the LAN as well. Rather than mapping `opengear:3001 to linux_server:5001`, you could map `device_reachable_from_opengear:443 to linux_server:5090`. This is handy for gaining OOB access to devices with only a GUI.
* Configure terminal emulator to “proxy” SSH connections through a particular host - our Linux Server
* Connect to device console/GUI directly from your workstation with ease

# Instructions
## Linux Server
I used Azure due to my Org’s relationships/policies, but this could be on AWS, Digital Ocean, GCP, Alibaba, whatever you want. I personally recommend that it exist outside your production network.

Resource requirements are almost nothing. Get the lowest tier available unless you have a reason to do otherwise. I suppose one could use Windows Server 2016 and [install OpenSSH](https://github.com/PowerShell/Win32-OpenSSH) on it and use that, if one was feeling particularly silly.

## OpenGear Direct SSH Access

## OpenGear Call Home
### Serial Ports
### Web Access to LAN

## Terminal Emulator