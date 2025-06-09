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

+ «FFmpeg playlist» – enable if you want to receive broadcasts that will be processed by the ffmpeg module of «TVLINK».

### «Streams»

<p align="center">
  <a href="/tvlink/pvr-client/03.png"><img src="/tvlink/pvr-client/03.png" width="480"/></a>
</p>

+ «TVLINK connection timeout» – the connection timeout of the client to the «TVLINK» server for retrieving the channel list. This option does not affect broadcasts.

+ «Buffering streams» – if activated, the client will additionally buffer streams (using Kodi's capabilities).

+ «FFmpegDirect for Timeshift» – enables the Timeshift function via the «Inputstream FFmpeg Direct» addon.

+ «FFmpegDirect for Catchup» – enables the Catchup function via the «Inputstream FFmpeg Direct» addon.

{{% hint info %}}
The last two options ("FFmpegDirect for ...") will only work if you activate the "Inputstream FFmpeg Direct" add-on. Otherwise, the client will ignore them.

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
You press the "left" button to the desired moment and watch the movie from the beginning.

+ «Catchup» is when you launch a TV program (that has already aired) from the "EPG".

In practice, «TimeShift» and «Catchup» also differ in the mode in which the "Kodi" player will operate.

+ «TimeShift» — the player operates in TV mode. This means that the player does not change its TV functionality (you started a channel and rewound).
For example, you can call up the channel list with the "left" button and the EPG with the "right" button. The "up/down" buttons will function as rewind/fast-forward.

+ «Catchup» — the player operates in VOD (Video On Demand) mode. This means that the player behaves as if you launched a regular video (you press the "Play programme" button in the EPG).
The "left/right/up/down" buttons work as rewind/fast-forward. They differ only in the rewinding interval.

{{% hint info %}}
«TimeShift» only works when the "FFmpegDirect for Timeshift" option is enabled. For IPTV archives (Catchup) to work, the "FFmpegDirect for Catchup" option is not mandatory.
{{% /hint %}}
