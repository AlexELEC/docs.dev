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

The last two options («FFmpegDirect for ...») will only work if the <a target='_blank' href="https://kodi.wiki/view/Add-on:Inputstream_FFmpeg_Direct">«Inputstream FFmpeg Direct»</a>
addon is installed. Otherwise, the client will ignore them.

«Timeshift» only works when the «FFmpegDirect for Timeshift» option is enabled. For IPTV archives (Catchup) to function, the «FFmpegDirect for Catchup» option is not mandatory.

{{% hint info %}}
The «Inputstream FFmpeg Direct» addon currently does not work correctly on some architectures, such as Intel.
If you activate «FFmpegDirect for Timeshift», the automatic stream switching within a channel will stop working.
The «Inputstream FFmpeg Direct» addon, through which the streams will pass, cannot automatically change stream parameters.
{{% /hint %}}

---

All other settings are the same as in the «PVR IPTV Simple» client.

<p align="center">
  <a href="/tvlink/pvr-client/04.png"><img src="/tvlink/pvr-client/04.png" width="480"/></a>
</p>
