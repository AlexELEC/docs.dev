---
title: Work Status and Program Updates
weight: 19
---

## Work Status and Program Updates

{{% hint info %}}
This information pertains to the settings on the «Status» and «About» pages.
{{% /hint %}}

## Program Work Status

<p align="center">
  <a href="/tvlink/status/01.png"><img src="/tvlink/status/01.png" width="480"/></a>
</p>

The table at the top of the «Status» page displays information about the program's usage of system resources.

By default, the information is updated every 5 seconds. You can select the desired interval from the «Refresh page (sec)» list.

+ «TVLINK uptime» – the time elapsed since the program was started (settings initialized).
+ «TVLINK uses memory» – the amount of RAM the program is using (in megabytes).
+ «TVLINK open sockets» – the number of currently open sockets.
+ «Free system memory» – the percentage of free RAM in the system. This refers to the entire system and its processes.

If stream broadcasting is currently in progress (clients are connected to the server), the «Active streams» table is displayed.

+ «Client» – the client's IP address and port.
+ «Channel» – the channel being broadcast to the client.
+ «Source» – the source from which the stream is being broadcast.
+ «Start Time» – the time when the broadcast was started.
+ «URL» – the address from which «TVLINK» retrieves the stream.

The red icon in the «Client» column allows switching the broadcast to the next stream for the client.

The «View program Logs» link (at the bottom of the page) opens the program's log page.

<p align="center">
  <a href="/tvlink/status/02.png"><img src="/tvlink/status/02.png" width="480"/></a>
</p>

## Program Update

The «About» page displays the program version, as well as links to download the playlist and EPG.

If a new version of the program is available, information about it and an «Update» icon will appear. Click this icon and wait for the program to update.

<p align="center">
  <a href="/tvlink/status/03.png"><img src="/tvlink/status/03.png" width="480"/></a>
</p>

During the update, all settings are preserved. Just in case, you can save your settings by copying the «tvlink/data» directory and restore it if necessary.

<p align="center">
  <a href="/tvlink/status/04.png"><img src="/tvlink/status/04.png" width="480"/></a>
</p>
