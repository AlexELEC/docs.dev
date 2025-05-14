---
title: Overview
weight: 10
---

## General info

«TVLINK Server» is an IPTV channel repeater and aggregator with a user-friendly web interface.
It retransmits streams specified by the user from sources such as IPTV playlists, Acestream, Ministra/Stalker Middleware, or add-ons.

The main goal of the program is to provide uninterrupted operation of IPTV channels. You can automatically
or manually combine streams of a single channel from various sources, and «TVLINK», depending on the source's
priority and its operability, will select and retransmit the best stream.

If the previous stream stops broadcasting for any reason, the program will automatically switch to the next
available stream of the same channel. This cycle will continue as long as at least one stream from the set is working.

The program supports IPTV archives (catchup) with the ability to switch to the next stream,
even if the archive types in these streams differ. Any IPTV player with support for the «Shift» archive
type is suitable for this function. Even if such a player does not support other archive types
(Append, Flussonic), it will still play them due to the internal conversion of archive types in «TVLINK».

The program also provides:

+ convenient setup and provision of EPG (Electronic Program Guide in XMLTV format)
+ built-in API for independent add-on development
+ unlimited number of users and IPTV sources (depends only on hardware capabilities)
+ ability (using profiles) to provide different sets of channels to different users
+ edit (change name, disable, delete) channels, groups (individually or in groups)
+ sort, set numbers for channels and groups, set icons for channels
+ ability to automatically (on a schedule) update channel sources and EPG
+ protection of your channels from unauthorized access using «tokens»
+ stream status and program log in the web interface

The program uses the Python module <a target='_blank' href="https://streamlink.github.io/">«Streamlink»</a>.
This, in turn, makes it possible to use a large number of <a target='_blank' href="https://streamlink.github.io/plugins.html">add-ons</a>
for «Streamlink» itself (those that do not require the support of the <a target='_blank' href="https://streamlink.github.io/api/webbrowser.html">«webbrowser»</a> submodule).
For example, watch live broadcasts of TV channels from YouTube and many other sources.

{{% hint info %}}
«TVLINK» can be used with any IPTV player, but to get all the benefits of the server, you should
use «PVR TVLINK Client» for Kodi.
{{% /hint %}}

{{% details "Program limitations." %}}
---
The program does not work in Russia and Belarus.
However, if you do not support Russian aggression in Ukraine, create a file named «_Glory_to_Ukraine_»
in the main «TVLINK» directory, for example:

    touch /opt/tvlink/Glory_to_Ukraine

This way, you will disable geolocation checking when the program starts.

{{% /details %}}

«TVLINK» <a target='_blank' href="https://github.com/AlexELEC/TVLINK-Releases/releases">releases</a> are compiled only for «Linux». The following architectures are supported:

+ x86-64
+ arm7
+ aarch64

The program does not require many resources. For example, when serving two clients, it averages 70 MB of RAM usage.
