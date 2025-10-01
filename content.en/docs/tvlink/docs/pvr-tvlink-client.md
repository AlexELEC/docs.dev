---
title: PVR TVLINK Client
weight: 20
---

## PVR TVLINK Client for Kodi

As a client (IPTV player) for «TVLINK», the «PVR TVLINK Client» for «Kodi» is the most suitable.
Only with this client will you get all the features of the «TVLINK» server.
Such as, for example, seamless switching of streams for the user (in case of broadcast failures) of the same channel with different audio and video formats.
The client supports Timeshift (pause/rewind), IPTV archives, and EPG.

<p align="center">
  <a href="/tvlink/pvr-client/01.png"><img src="/tvlink/pvr-client/01.png" width="480"/></a>
</p>

<a target='_blank' href="https://github.com/AlexELEC/pvr.tvlink">The client code</a> is based on <a target='_blank' href="https://github.com/kodi-pvr/pvr.iptvsimple">«PVR IPTV Simple»</a>
but is designed to meet all the requirements of «TVLINK».
For example, the client will never disconnect from the «TVLINK» server on its own.
This will only happen when the user switches the channel or stops the channel broadcast.

{{% hint warning %}}
A modified version of «Kodi» is required for «PVR TVLINK Client» to work; it will not function with the original version of «Kodi».
{{% /hint %}}

## Configuration

### «General»

<p align="center">
  <a href="/tvlink/pvr-client/02.png"><img src="/tvlink/pvr-client/02.png" width="480"/></a>
</p>

+ «TVLINK IP-address» – the IP address of the «TVLINK» server.
+ «TVLINK port» – the port of the «TVLINK» server.
+ «TVLINK profile» – the user profile on the «TVLINK» server. If not specified, the main profile (main) is used.
+ «Auth. Token» – the authorization token, if required.

### «Streams»

<p align="center">
  <a href="/tvlink/pvr-client/03.png"><img src="/tvlink/pvr-client/03.png" width="480"/></a>
</p>

+ «TVLINK connection timeout» – the connection timeout of the client to the «TVLINK» server for retrieving the channel list. This option does not affect broadcasts.

+ «Buffering streams» – if activated, the client will additionally buffer streams (using Kodi's capabilities).

+ «Use Inputstream FFmpeg Direct» – enabling this parameter activates the Timeshift and Catchup functionalities using the «Inputstream FFmpeg Direct» add-on.

{{% hint info %}}
This last option («Use Inputstream FFmpeg Direct») will only work provided that you activate the «Inputstream FFmpeg Direct» add-on.
Otherwise, the client will ignore these features.

The "Inputstream FFmpeg Direct" add-on has been specifically modified to work with "TVLINK" and is embedded in the system.
If you update it to the original version, it will lose its functionality regarding "TVLINK".
{{% /hint %}}

All other settings are the same as in the "PVR IPTV Simple" client.

<p align="center">
  <a href="/tvlink/pvr-client/04.png"><img src="/tvlink/pvr-client/04.png" width="480"/></a>
</p>

## «TimeShift» and «Catchup» Functions

These functions allow you to rewind (and then fast-forward) live broadcasts if your IPTV provider offers the "IPTV archives" service.

+ «TimeShift» is rewinding directly while you are watching a TV channel. For example, you started a channel where a movie has already been playing for 30 minutes.
You press the "down" button to the desired moment and watch the movie from the beginning.

+ «Catchup» is when you launch a TV program (that has already aired) from the "EPG".

{{% hint info %}}
«TimeShift» only works when the "Use Inputstream FFmpeg Direct" option is enabled. For IPTV archives (Catchup) to work, the "Use Inputstream FFmpeg Direct" option is not mandatory.
{{% /hint %}}
