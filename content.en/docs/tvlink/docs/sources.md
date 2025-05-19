---
title: Channel Sources Configuration
weight: 13
---

## Channel Sources Configuration

On the «Sources» page, you have the ability to configure the following:

+ Playlists sources
+ Addons sources
+ Stalker/Ministra portals sources
+ AceStream sources
+ [Channel picons](/docs/tvlink/docs/channels/#picons-utility)
+ [XMLTV EPG sources](/docs/tvlink/docs/epg/)
+ [User Profiles](/docs/tvlink/docs/profiles/)

## Playlists Sources

Activate the «Playlists sources» switch. Click the «Add playlist» button.

<p align="center">
  <a href="/tvlink/sources/01.png"><img src="/tvlink/sources/01.png" width="480"/></a>
</p>

In the «Add new playlist» window:

+ Enter the playlist name. It must consist of Latin letters, without special characters (spaces, hyphens, etc.),
and cannot start with a digit.
+ Enter the playlist URL. If the playlist file is saved on your local computer, the address format should be as
follows: «file:///path_to/your_playlist_file» (for example, file:///Data/list/playlist.m3u).

Click the «Save changes» button.

<p align="center">
  <a href="/tvlink/sources/02.png"><img src="/tvlink/sources/02.png" width="480"/></a>
</p>

## Addons sources

Click the «Add addon» button. In the «Add new addon» window, click (double-click may be required for some browsers)
in the «Addon name» field. The list of available addons in the repository will appear.
Select the desired addon and click «Save changes».

<p align="center">
  <a href="/tvlink/sources/03.png"><img src="/tvlink/sources/03.png" width="480"/></a>
</p>

{{% hint info %}}
You can also create your own addon. Refer to the following section for instructions on how to do this.
{{% /hint %}}

## Stalker/Ministra portals sources

Click the «Add portal» button. In the «Add new Portal (Stalker Middleware)» window, enter the following data:

+ Portal name. It must consist of Latin letters, without special characters (spaces, hyphens, etc.), and cannot start with a digit.
+ Portal url.
+ MAC address for portal access (User MAC).

The optional «Use HLS streams» toggle allows receiving HLS streams if the Portal supports this method.
During the creation stage, it is recommended not to enable this option if there is no certainty that the Portal supports HLS streams.

<p align="center">
  <a href="/tvlink/sources/04.png"><img src="/tvlink/sources/04.png" width="480"/></a>
</p>

After you click the «Save changes» button, a file with your portal's name will be created in the «tvlink/scrapers» directory.
For example, «tvlink/scrapers/Portal.py». This file contains three variables that you can edit (this is optional):

+ INCLUDE_GROUP is a list of channel groups that you want to receive.
All other groups will be ignored (will not be included in the list).
Please note that an exact match will be checked, considering the case of the characters.

+ EXCLUDE_NAME is a list where you can specify characters that will be excluded from the channel name.
For example, if the channel name is «US Discovery HD», and you want to have «Discovery HD», set EXCLUDE_NAME = ['US '].
Note that in this example, there is a space at the end of 'US '.

+ DEFAULT_LOGO is the URL address of the icon that will be applied to channels where the icon is missing,
or if the «Disable load icons» option is enabled in the source settings.

{{% hint info %}}
After editing these variables, you need to click «Apply Settings» on the «Settings» page, or restart the application.
{{% /hint %}}

<p align="center">
  <a href="/tvlink/sources/05.png"><img src="/tvlink/sources/05.png" width="480"/></a>
</p>

After creating the Portal, you can change the «Portal url», «User MAC», «Use HLS streams», «Disable load icons»,
and «Repeat source streams» options without restarting the settings.
However, you need to update the source (click the «Update» icon).

<p align="center">
  <a href="/tvlink/sources/06.png"><img src="/tvlink/sources/06.png" width="480"/></a>
</p>

+ «Disable load icons»: disables fetching channel icons from the portal. Some portals may have non-valid icon addresses specified.
This leads to a delay (depending on your browser) in displaying channel lists in the program's web interface.

+ «Repeat source streams»: allows setting the number of stream playback repetitions during failures.
This option is unrelated to the Streamlink option, «Stream retry count». Value «always» — repetitions are unlimited,
«0» — the function is disabled (default), other values — the number of repetitions.

{{% hint info %}}
If your channel has only one stream and if that stream is working in some way, «TVLINK» will endlessly try to restart that stream.
The «Repeat source streams» function does the same for the source (the stream of this source) of a channel where there is more than one stream.
Thus, switching to the next stream of this channel will occur if either the stream has completely stopped working or after the number of repetitions
you have selected. If «always» is selected — then only if the stream has stopped providing anything at all.
{{% /hint %}}

## AceStream sources

Click the «Add Acestream» button. In the «Add new AceStream source» window, enter:

+ Source name. It should be in Latin letters, without special characters (spaces, hyphens, etc.) and cannot start with a digit.

+ The URL address of the <a target='_blank' href="https://wiki.acestream.media/Main_Page">«AceStream»</a> server in the format http://ip-address:port (for example: «http://192.168.1.1:6878»).

+ The optional «Use HLS streams» switch allows receiving HLS streams.
It is not recommended to enable if the «AceStream» server is running on your local network, as this will significantly increase the channel switching time.

After you click the «Save changes» button, you can enter the channel group(s) you want to receive in the «Channel Categories (comma-delimited)»
field in the source settings. This field is empty by default, which means that all channels from all groups will be loaded (approximately 3000 of them).
You can find the names of the official groups <a target='_blank' href="https://wiki.acestream.media/Channel_Category">here</a>.
Users who broadcast streams can create their own group names or completely ignore group creation.
Therefore, if you need all the channels that are in the «AceStream» database, then leave the «Channel Categories (comma-delimited)» field empty.

<p align="center">
  <a href="/tvlink/sources/07.png"><img src="/tvlink/sources/07.png" width="480"/></a>
</p>

The channel database is loaded directly from the <a target='_blank' href="https://wiki.acestream.media/Search_API">«AceStream Server-side Search API»</a>
and does not depend on other resources (for example: pomoyka.i2p).

## Sources Table

After the channel source is created, you will see the following table:

<p align="center">
  <a href="/tvlink/sources/08.png"><img src="/tvlink/sources/08.png" width="480"/></a>
</p>

+ «Name» – the name of the source, settings and deletion of this source. When the source is active and updated, its name becomes a link to editing ('mapping') the channels for this source.
The settings icon is displayed in blue if the source has default stream settings, and in green if the user has changed the parameters.
+ «Catchup» – archive selection. Supported types: «Append», «Shift», and «Flussonic».
+ «Enable» – enables or disables the source.
+ «Prio» – source priority. The smaller the value, the higher the priority.
+ «Limit» – limits client access to the source. The value is the maximum number of clients who can watch simultaneously from this source.
+ «Add channels» – if this switch is enabled and you update the source, all the source's channels will be automatically added to the «TVLINK» channel list ('channel mapping').
This only works with manual (forced) channel updates, but this option is ignored during automatic updates.
+ «New channels» – if this switch is enabled, new channels will be added to the «TVLINK» channel list upon source update, if they appear in this source.
+ «Update period» – time (in hours) after which the source will be automatically updated. Zero means that the update is disabled.
+ «Update» – immediate update of the source, as well as the time of the last update.
+ «Links» – the number of links to streams (channels) that this source contains.

## Adding Channels to the List

There are two ways you can add channels from the source to the «TVLINK» channel list (channel mapping):

1. Enable the «Add channels» switch and click «Update». In this case, all the source's channels will be automatically added to the «TVLINK» channel list.
2. Update the source by clicking «Update». After this, the source name becomes a link to a page where you can add channels manually.

<p align="center">
  <a href="/tvlink/sources/09.png"><img src="/tvlink/sources/09.png" width="480"/></a>
</p>

The «Map» switch adds a channel to the «TVLINK» channel list; when adding channels, a group is created to which the channel belongs, and its icon is transferred.

## Automatic Channel Merging

«TVLINK» automatically merges channels with the same names. Therefore, the number of source channels («Links») does not always correspond to the number of channels in the «TVLINK» list.
During merging, character case and spaces in the channel name are ignored. For example, all channels with the following names will be considered one and the same channel:

+ Channel 25
+ CHANNEL 25
+ ChaNNel25

{{% hint info %}}
If channel groups are present in the source, they will also be exported.
If there are no groups, all channels from the source will be assigned a group with the name of the source itself.
{{% /hint %}}

## Channel Archives (Catchup)

If your IPTV provider offers this feature, select one of the archive types:

+ «Append»
+ «Flussonic»
+ «Shift»
+ «none» — means the function is disabled.

You can find out what type of archive you have from your IPTV provider.

«TVLINK» supports automatic switching of archive streams during a failure, regardless of the archive types.
This means that if there is a problem with an archive stream from a source where the type is «Shift», it will switch to an archive stream from a source with «Flussonic».
The switching order depends on the priority of the sources. That is, the same functionality as with regular streams.

If you are using a third-party IPTV player (not PVR TVLINK Client), you need to set the archive type to «Shift» in its settings.
That is, «TVLINK» itself, regardless of the archive type of the source, will output archives in the «Shift» format.

## Source Priority (Prio)

If both sources contain the same channel, the stream from the source with a higher priority (lower number) will be used first.
If this stream is not working or has stopped broadcasting during operation, «TVLINK» will switch to the next source with a lower priority, and so on, in a loop.

## Source Connection Limit (Limit)

If the source has a limit on the number of connections to streams, set the required value.
This is necessary so that your IPTV provider does not block your access. «TVLINK» will automatically switch to the next stream if the limit is exceeded.

«TVLINK» switches channels in asynchronous mode; this means that the program does not wait for the previous stream to close before opening the next one.
Otherwise, channels would switch very slowly.
Client identification occurs via their IP addresses.
These two facts impose certain limitations on the operation of the «Limit» option.
Namely: for clients who have the same IP address, «TVLINK» automatically increases the connection limit.
In the program's operation log, you will see the following entry:

    Increase MaxStream count [1+1 HD] from [MySouce]: set max stream [2] - limit [1]

This means that a limit of one connection is set for the «MySouce» source.
But since the previous stream has not yet closed when switching channels, «TVLINK» automatically increased the limit (by one).
If this had not happened, the «MySouce» source would not have been available at that moment.

Also, if two clients have the same IP address (two IPTV players are running on the same machine) and make a request to the same source,
the limit of this source will also be increased by one. This is because «TVLINK» cannot determine whether it is a request to switch channels
from the same client or a request from another client, as their IP addresses are the same.

## Bottom of the «Sources» Page

+ «Update all sources» – click if you need to update all channel sources at once.
If the «Create static playlist» option is enabled in the server settings (Settings), a static playlist will also be created.
+ «Create static playlist» – if you have the «Create static playlist» option enabled in the settings (Settings page),
the «Create static playlist» link will appear at the bottom of the sources page (Sources).
This allows you to update the static playlist without updating all sources.
