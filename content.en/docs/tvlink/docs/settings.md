---
title: Server and Stream Configuration
weight: 18
---

## Server Configuration

{{% hint info %}}
This information pertains to the settings on the «Settings» page.
{{% /hint %}}

<p align="center">
  <a href="/tvlink/settings/01.png"><img src="/tvlink/settings/01.png" width="480"/></a>
</p>

{{% hint info %}}
For most settings on this page, you need to reread the «TVLINK» configuration for the changes to take effect. There is an «Apply Settings» option at the bottom of the page for this.
The «Refresh sources at playlist» and «Remove broken channels» options do not require this.
{{% /hint %}}

+ «Server port» – defines the port on which «TVLINK» accepts requests. The port for streams will be one greater: «Server port + 1».

+ «Playlist IP» – this is the address that «TVLINK» will use for playlists (when «Auto playlist IP» is disabled). The address can be selected from the list.

+ «Auto playlist IP» – if this option is enabled, «TVLINK» will use the IP address in the playlist from which the client's request originates.

+ «Check internet IP» – the IP address that «TVLINK» uses to check the internet connection. The default address is «8.8.8.8».
If you need to change this address before running the program, create a file named «check-internet.ip» in the tvlink directory and enter the required address there.

+ «Check internet max time» – the maximum time during which «TVLINK» checks the internet connection. The program will not start until it has internet access.

+ «Refresh sources at startup» – refresh sources when the program starts.

+ «Refresh sources at playlist» – refresh sources when a playlist is requested.

+ «Create static playlist» – creates static playlist files (main and for profiles) in the «tvlink/playlist» directory and serves them upon client requests.
This significantly speeds up operation when you have a large number of channels (100 or more).
The static playlist is created (updated) each time the channel sources are automatically updated, or when you click «Update all sources/Create static playlist» on the «Sources» page.
Static playlists are not created for tokens (Authentication Token).

+ «Remove broken channels» – «TVLINK» will automatically delete all channels that are found to be non-functional.
Be cautious with this option: if the internet connection is lost, «TVLINK» will start deleting every channel you try to turn on.

+ «Authentication webUI» – simple authentication (login/password) for the web interface.
After activation, you will immediately see a window to enter your credentials. You need to enter – «admin/admin».
After that, you can specify your own login and password in the «Login (webUI)» and «Password (webUI)» fields respectively.
If you enter an empty string or less than three characters in the «Login (webUI)» field, the login will be reset to the default value (admin).
The same applies to the «Password (webUI)» field: an empty string or less than three characters will reset the password to «admin».

IP addresses for the «Playlist IP» list are taken from the system.
If you need to add an IP address (or a domain name) that is not in the system (for example, if «TVLINK» is running behind NAT), create a file named «ip-address.ext» in the «tvlink/data» directory.
Each line of the file must contain one IP address or one domain name. For example:

    100.100.100.100
    200.200.200.200
    my.own.server.com

## Authentication Token for Streams and Playlists

<p align="center">
  <a href="/tvlink/settings/02.png"><img src="/tvlink/settings/02.png" width="480"/></a>
</p>

Protection against unauthorized access to streams and playlists.

+ «Authentication Token» – enables support for authentication tokens.
+ «Main Token for playlist/streams» – any sequence of case-sensitive Latin letters and/or digits.

{{% hint info %}}
After any changes to the «Tokens» settings, you need to apply the settings («Apply Settings» at the bottom of the page) or restart the program.

If you have the «Create static playlist» option enabled, then after any changes to the «Tokens» settings, do not forget to update the static playlists (click «Update all sources» on the «Sources» page).
{{% /hint %}}

If the «Authentication Token» option is activated, after applying the settings, access to streams and playlists will only be possible via the token. The token for the main playlist is set on the «Settings» page.

Other tokens are set in the [«User Profiles»](/docs/tvlink/docs/profiles) section.

## Periodic Settings Reload

<p align="center">
  <a href="/tvlink/settings/03.png"><img src="/tvlink/settings/03.png" width="480"/></a>
</p>

This function reloads the «TVLINK» settings at specified time intervals. This action is similar to clicking the «Apply Settings» button at the bottom of the page.
It does not restart the program itself, but only re-initializes all settings. However, this helps to clear the RAM and close all network connections (sockets).
Therefore, this function can be useful when the server operates 24/7.

+ «Reload by interval» – reloads the «TVLINK» modules after a time interval (in hours) specified in the «Reload every hours» parameter.
+ «Reload once a day» – reloads once a day at the time specified by the «Reload at o’clock» parameter.

The time specified in these options is approximate. For example, if «Reload once a day» / «Reload at o’clock» is set to 4 o'clock, the reload will occur between 4:00 and 5:00.

The «Reload once a day» option has a higher priority. If you enable both parameters, the module reload will occur once a day.

Reloads occur only under the following conditions:

1. the number of open network connections (sockets) exceeds 10;
2. the program uses more than 60 MB of RAM for systems with less than 1.5 GB of RAM, and more than 120 MB for systems with more than 1.5 GB of RAM;

To avoid problems with stream broadcasting, these functions will only trigger if «TVLINK» is not currently broadcasting (no clients are connected).
The module reload will occur immediately after the last client disconnects.

If the «Ignore connected clients on Reload» option is enabled, the «TVLINK» modules will be reloaded regardless of whether there are connected clients.


## «Empty channel link»

Allows you to enter your own link to a stream that will be played if none of the main channel links are working.

## «Exclude these lines from channel names when mapping»

Excluding words from channel names. You can exclude any lines from a channel name for automatic linking.
The channel name itself remains unchanged, however, during automatic linking, «TVLINK» will discard the part you specified from the name.
The delimiter for words that need to be excluded from the name is a comma (without spaces).
For example, with these settings, all channels with the following names will be considered the same channel – «Discovery Science HD».

    «Discovery Science HD»
    «Discovery Science HD orig»
    «Discovery Science HD PREMIUM+»

<p align="center">
  <a href="/tvlink/settings/04.png"><img src="/tvlink/settings/04.png" width="480"/></a>
</p>

{{% hint info %}}
If there are channels in one source as shown above, then the stream (link to the stream) with the longest name will have the highest priority, i.e.,
first «Discovery Science HD PREMIUM+», then «Discovery Science HD orig», and lastly «Discovery Science HD».
{{% /hint %}}

## «M3U playlist settings»

Allows you to add the elements you need after the «EXTM3U» and «EXTINF» tags in the «TVLINK» playlist.
For example, this could be information for periodic updating of the channel list: «refresh="3600"». Provided that your IPTV player supports this.

## Stream Settings

<p align="center">
  <a href="/tvlink/settings/05.png"><img src="/tvlink/settings/05.png" width="480"/></a>
</p>

+ «Main User-Agent» – sets the default User-Agent. Some IPTV providers may have blocking based on the "user-agent".
They provide the stream only if the request comes from a specific application. You can specify «TVLINK» so that it identifies itself as another application.

The following settings mostly relate to the «Streamlink» module and are responsible for working with streams.

+ «Stream Ring buffer» – sets the buffer size for streams (in megabytes).
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-ringbuffer-size">«ringbuffer-size»</a> parameter in «Streamlink».

+ «Chunk size» – sets the fragment size when reading a stream (in bytes). The larger the fragment size, the lower the CPU load.
The smaller the fragment size, the faster the stream opens.

+ «Threads job timeout» – the time (in seconds) after which the chain of reading/writing stream fragments will be stopped.
Partially corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-stream-timeout">«stream-timeout»</a> parameter in «Streamlink».

+ «General HTTP timeout Connect/Data» – the general timeout (in seconds) used for all HTTP requests, except those covered by other parameters.
For understanding: in HLS streams, this will be the timeout for obtaining the segment list.
The time (timeout) for connection and the time for receiving data are set separately, respectively.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-http-timeout">«http-timeout»</a> parameter in «Streamlink»,
except that it allows setting different values for connection and data reading.

+ «HLS segment timeout Connect/Data» – the timeout (in seconds) used for HLS segments (as well as DASH, etc.).
The time (timeout) for connection and the time for receiving data are set separately, respectively.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-stream-segment-timeout">«stream-segment-timeout»</a> parameter in «Streamlink»,
except that it allows setting different values for connection and data reading.

+ «HLS segment queue threshold» – the multiplication factor of the target duration of the HLS playlist,
after which the stream will be stopped prematurely if no new segments are added to the queue after the playlist update.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-segment-queue-threshold">«hls-segment-queue-threshold»</a> parameter in «Streamlink».

+ «Stream retry count» – this option sets the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-stream-segment-attempts">«stream-segment-attempts»</a>
and <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-playlist-reload-attempts">«hls-playlist-reload-attempts»</a> parameters for «Streamlink».
That is, the number of download attempts for segments and the segment list.

+ «Segment threads» – the number of parallel segment downloads.
This is the size of the thread pool used for downloading segments.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-stream-segment-threads">«stream-segment-threads»</a> parameter in «Streamlink».

+ «Segments Queue» – the size of the segment queue. In «Streamlink», it is fixed at 20 segments.
But this is too much for Live streams. The smaller the queue, the sooner streams will close, and there will also be less RAM consumption and fewer open sockets.
It is better to set it to «as threads», which corresponds to the number of «Segment threads» but not less than 6 segments.

+ «HLS live edge» – specifies how many HLS segments need to be downloaded when the stream starts.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-live-edge">«hls-live-edge»</a> parameter in «Streamlink».

+ «HLS playlist reload time» – controls the time after which a request is made to update the segment list.
Partially corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-playlist-reload-time">«hls-playlist-reload-time»</a> parameter in «Streamlink».
The «segment» parameter has the same meaning as in «Streamlink». The «duration» value corresponds to «default» in «Streamlink».
The «average» value is the average time of two segments. The «default» value is either one of the values
corresponding to «duration» / «segment», or, if they are not present, the set time is 6 seconds.

+ «HLS Stream Data» – if activated, immediately transfers data from the segment to the output buffer during download.
Channels open quickly, without prior buffering before starting. If disabled, data is transferred only after the first segment is downloaded.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-segment-stream-data">«hls-segment-stream-data»</a> parameter in «Streamlink».

+ «HLS Live Restart» – if active, go to the beginning of the live broadcast or as far back as possible.
Corresponds to the <a target='_blank' href="https://streamlink.github.io/cli.html#cmdoption-hls-live-restart">«hls-live-restart»</a> parameter in «Streamlink».

+ «Debug Streams» – adds the «Streamlink» module's log to the «TVLINK» log. The log file is located in the «tvlink/log» directory.

+ «Sources Proxy» and «Streams Proxy» – allow you to set a proxy for sources and streams. Format: «http://login:password@your.proxy:port».
The «login/password» values are optional. Supported protocols: http, https, socks5.

## Stream settings for individual sources

<p align="center">
  <a href="/tvlink/settings/06.png"><img src="/tvlink/settings/06.png" width="480"/></a>
</p>

Stream settings such as:

+ Threads job timeout
+ General HTTP timeout
+ HLS segment timeout
+ HLS segment queue threshold
+ Stream retry count
+ HLS live edge
+ HLS Stream Data
+ HLS Live Restart

can be set individually for each source on the «Sources» page (icon next to the source name). In this case, there is no need to click «Apply Settings»; the changes take effect immediately.

These same parameters do not require a reload on the «Settings» page either.

The «Default» button in the «Streamer settings» form returns all individual stream settings for the source to the main settings on the «Settings» page.

+ Playlist URL – allows you to change the URL address of the source.

+ User-Agent – allows you to set the “User-Agent” option for each source (streams within this source) individually. This overrides the «Main User-Agent» option.

+ «Disable load icons» — disables fetching channel icons from the source. Some sources may have invalid icon addresses specified.
This leads to a delay (depending on your browser) in displaying channel lists in the program's web interface.

+ «Repeat source streams» — allows you to set the number of times a stream playback will be repeated during failures. This option is not related to the Streamlink option «Stream retry count».
The value «always» means that repeats are unlimited, «0» — the function is disabled (by default), other values are the number of repeats.

{{% hint info %}}
If your channel has only one stream and if that stream is working in some way, «TVLINK» will endlessly try to restart that stream.
The «Repeat source streams» function does the same for the source (the stream of this source) of a channel where there is more than one stream.
Thus, switching to the next stream of this channel will occur if either the stream has completely stopped working or after the number of repetitions
you have selected. If «always» is selected — then only if the stream has stopped providing anything at all.
{{% /hint %}}

Changes to these field settings take effect immediately after the field loses focus.

## Explanation of stream configuration

First, let's define the differences between connection timeouts and read data timeouts (Connect timeout and Read Data timeout).

+ «Connect timeout»

When a client (in this case, TVLINK is a client in relation to the server from which it requests streams) initiates a connection, it must receive a response from the server (a specific response code).
It does not matter what specific response comes from the server. This could be a 200 (connection established), 302 (redirection), or any other response, the main thing is that the server responds.
If a response from the server is not received within the time period specified in the connect timeout (connection timeout period), the client drops the connection.

+ «Read Data timeout»

When the client receives a 200 (connection established) response from the server, it begins to download (read) the data that the server sends.
If the server does not transmit information within the time period specified in the read data timeout (read data timeout period), the client drops the connection.

Now let's define the stream formats.

The most common ones are TS and HLS.

+ «TS»

Essentially, this is the same as if you were downloading any file in a browser.
The client makes a request and, if it receives a 200 response, simply receives the data sequentially.
The data is transmitted in a single stream, and if traffic issues arise, this causes problems with the video playback as well.
That is, for IPTV over the internet, this is not the best solution. It is more suitable for a local network.

+ «HLS»

This is the same «TS» (simplified, of course), but cut into chunks (segments).
Due to the fact that these segments are already recorded files (unlike TS, which is transmitted in real-time) and there are several of them, the client has the ability to download multiple segments simultaneously.
This, in turn, helps to cope with traffic problems and, accordingly, is better suited for IPTV over the internet.

Now, directly about the «TVLINK» parameters.

+ «General HTTP timeout Connect/Data»

If you have a TS stream, these timeouts will be applied. «HLS segment» timeouts will not be used for such streams.
If you have an HLS stream, the «General HTTP» timeouts will work when you receive playlists with a list of segments or stream quality options
(the provider may offer several stream quality options for different connection speeds). We call playlists text files that contain links to other playlists
(for example, if it is a list of stream qualities) or links to video segments.

+ «HLS segment timeout Connect/Data»

These timeouts are applied directly to segments (video files). Although the name of this parameter includes «HLS», these timeouts also work with other segmented stream formats, for example, «DASH».

In a simple case (without a stream quality list) for HLS streams, it will look like this:

+ getting the segment list – «General HTTP timeout»
+ downloading segment 1 – «HLS segment timeout»
+ downloading segment 2 – «HLS segment timeout»
+ downloading segment 3 – «HLS segment timeout»
+ getting a new segment list – «General HTTP timeout»
+ downloading segment 4 – «HLS segment timeout»
+ downloading segment 5 – «HLS segment timeout»
+ downloading segment 6 – «HLS segment timeout»
+ getting a new segment list – «General HTTP timeout»

and so on…

+ «HLS segment queue threshold»

This parameter (timeout) also applies to HLS streams. The HLS segment list (playlist) contains a variable indicating the duration of the video in the segment.
This variable is used by «TVLINK» to determine after what time to request a new segment file. The server constantly updates this list immediately after a new segment recording is finished.
«HLS segment queue threshold» - this is the number by which the segment duration variable will be multiplied.
If the segment list on the server is not updated within the time obtained by this multiplication, the client will drop the connection.
For example, the list specifies that the segment duration is 6 seconds. If the «HLS segment queue threshold» is set to three, the client will drop the connection after 18 seconds if a new segment does not appear on the server.

+ «Threads job timeout»

This is the timeout of the internal «Streamlink» loop that reads data from the input and writes it to the output stream.
If no data passes through the loop within the specified time, it stops working, which results in the closure of any connection.

+ «Stream retry count»

This is the number of connection retries when the «General HTTP» and «HLS segment» timeouts are triggered.

## FFmpeg transcode stream

If «FFmpeg» is installed on your system, you have the option to enable the «FFmpeg transcode stream» module.

<p align="center">
  <a href="/tvlink/settings/07.png"><img src="/tvlink/settings/07.png" width="480"/></a>
</p>

Options are FFmpeg command-line parameters. Field descriptions:

+ «Before input» – parameters for hardware transcoding
+ «Video encoder» – video encoder parameters
+ «Audio encoder» – audio encoder parameters

To understand how these parameters will be inserted into the «FFmpeg» command line, here is an example (simplified scheme):

    /usr/bin/ffmpeg -err_detect ignore_err -stream_loop -1 [Before input] -i http://channel.stream -c:v [Video encoder] -c:a [Audio encoder] -ignore_unknown -map 0:v -map 0:a -f mpegts

By default, the «Video encoder» and «Audio encoder» fields contain the “copy” parameter. That is, if these fields are left empty, the value “copy” will be set (skip the stream without transcoding).

Before setting values, make sure that «FFmpeg» on your system supports the respective parameters. For example, execute the command:

    ffmpeg -hide_banner -encoders

to view the available audio and video encoders.

If the processor in your system (for example, Intel Pentium N5000) supports hardware stream encoding, you can apply the following settings, for example.

«Before input»:

    -hwaccel vaapi -hwaccel_output_format vaapi -hwaccel_device /dev/dri/renderD128

«Video encoder»:

    h264_vaapi -r 50

«Audio encoder»:

    aac -b:a 96k

After applying the settings («Apply Settings»), on the «About» page a link to «M3U FFmpeg Playlist» will appear (format: http://ip-address:port/ffmpeglist).

<p align="center">
  <a href="/tvlink/settings/09.png"><img src="/tvlink/settings/09.png" width="480"/></a>
</p>

Enabling «FFmpeg transcode stream» does not affect the main broadcasting module. They work in parallel.
You can simultaneously connect some clients to the regular playlist (playlist) and others to the «FFmpeg» playlist (ffmpeglist).

{{% hint info %}}
You can always get the playlist via the link «http://ip-address:port/ffmpeglist», even if «FFmpeg transcode stream» is disabled and «FFmpeg» is not installed on the system. Therefore, be careful.
{{% /hint %}}

If you enable «Debug Streams» and run «TVLINK» from the command line, information from «FFmpeg» (encoding parameters, errors, etc.) will be displayed when the stream stops.

## EPG Update

<p align="center">
  <a href="/tvlink/settings/08.png"><img src="/tvlink/settings/08.png" width="480"/></a>
</p>

These settings are responsible for the periodic update of the «EPG».

+ «Auto update EPG» – enable/disable automatic periodic EPG update.

+ «Update period EPG» – select the update period from the list in hours, or once a day (at night).
