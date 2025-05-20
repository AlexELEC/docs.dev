---
title: TVLINK Simple Control
weight: 21
---

## «TVLINK Simple Control» Addon for Kodi

The addon can be installed from the <a target='_blank' href="https://github.com/AlexELEC/repo-21/tree/master/Omega/common">«AlexELEC Common Add-ons»</a> repository,
which is present in «LibreELEC/CoreELEC (ae-fork)» systems.

<p align="center">
  <a href="/tvlink/tvlink-control/01.png"><img src="/tvlink/tvlink-control/01.png" width="480"/></a>
</p>

Allows you to control channel streams (turn on/off) and shows (highlights in yellow) the link to the stream that is currently being broadcast.

<p align="center">
  <a href="/tvlink/tvlink-control/02.png"><img src="/tvlink/tvlink-control/02.png" width="480"/></a>
</p>

It also provides the ability to:

+ sequentially switch channel streams;
+ update «TVLINK» channel sources;
+ display information about clients connected to «TVLINK»;
+ display information about RAM and socket usage.

<p align="center">
  <a href="/tvlink/tvlink-control/03.png"><img src="/tvlink/tvlink-control/03.png" width="480"/></a>
</p>

## Configuration

<p align="center">
  <a href="/tvlink/tvlink-control/04.png"><img src="/tvlink/tvlink-control/04.png" width="480"/></a>
</p>

+ «IP-address TVLINK» – the IP address of the «TVLINK» server
+ «Port TVLINK» – the port of the «TVLINK» server

{{% hint info %}}
If «IP-address TVLINK» is not specified, «TVLINK Simple Control» uses the address «127.0.0.1».
{{% /hint %}}

In modified (ae-fork) ELEC systems, the addon is called by a long press of the «i» (info) button on the keyboard.
For remote controls in these systems, the following settings are made in the «keyboard.xml» file in Kodi.

    <FullscreenLiveTV>
        <keyboard>
            …
            <i mod="longpress">RunAddon(script.tvlink.conrol)</i>
        </keyboard>
    </FullscreenLiveTV>
