---
title: Entware
weight: 12
---

## Entware

{{% hint info %}}
The <a target='_blank' href="https://entware.net/about.html">«Entware»</a> repository provides the ability to easily install additional software on «LibreELEC/CoreELEC» systems.

A list of available packages can be viewed <a target='_blank' href="https://bin.entware.net/x64-k3.2/Packages.html">here</a>.
{{% /hint %}}


### Example of installing the «BitTorrent» client «Transmission»

Installing «Entware»:

    installentware

At the end, the following question will appear:

    Would you like to reboot now to finish installation (recommended) [y/N]?

For now, answer «No», just press «Enter».

Installing <a target='_blank' href="https://transmissionbt.com/">«Transmission»</a>:

    opkg install transmission-web

Rebooting the system:

    reboot

In your browser, enter the address «http://your-ip-address:9091» and use it.

<p align="center">
  <a href="/alexelec/entware/01.png"><img src="/alexelec/entware/01.png" width="480"/></a>
</p>

If you need to remove «Entware»:

    systemctl stop entware
    rm -fr /opt/*
    reboot
