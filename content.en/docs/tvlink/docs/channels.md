---
title: Channels
weight: 16
---

## Channels

{{% hint info %}}
This information pertains to the settings on the page «Channels».
{{% /hint %}}

<p align="center">
  <a href="/tvlink/channels/01.png"><img src="/tvlink/channels/01.png" width="480"/></a>
</p>

{{% hint warning %}}
Channel lists on all interface pages are displayed in batches of 200 channels per page (there are buttons at the bottom for navigating between pages).
When channels are deleted or linked, the pages themselves are not refreshed; only the elements are removed. This is done to speed up performance,
so you don't have to wait for the page to reload after each action. However, this can lead to some confusion. For example, if you have a list of 300 channels:
200 channels on one page and 100 on the other, if you delete 10 channels from the first page, you will see 90 channels when you navigate to the second page.
When the page is refreshed, the list is read again, and the first page will again have 200 channels, while the second will have the rest.

Before performing the setup on this page, please wait for it to load completely.
Links to channel logos from some sources may not work, which increases the page loading time in the browser.
Your changes will not be applied until the page is fully loaded.

Just keep this in mind while editing.
{{% /hint %}}

## Channel Logos

To set or change a channel logo, click the icon in the «Logo» column.
In the form that appears, you can specify the URL address of the desired image and click «Save changes».
It is preferable to use images in «png» format, but other formats (jpg, gif, bmp) are also allowed.

<p align="center">
  <a href="/tvlink/channels/02.png"><img src="/tvlink/channels/02.png" width="480"/></a>
</p>

If you have copied your own channel logos to the «tvlink/logos» folder, then by clicking the «Local logos» button, you can associate a channel logo.

<p align="center">
  <a href="/tvlink/channels/03.png"><img src="/tvlink/channels/03.png" width="480"/></a>
</p>

The highest priority is given to icons located in the «tvlink/logos» directory and having the format «Channel-ID.png» (for example: 7B7ADBFF.png).
You can see the «Channel-ID» in the «ID» column. If such an icon does not exist, «TVLINK» uses the icon you specified above.

If a channel does not have an icon, it will be automatically added when you perform a force update of any source with the «Add channels» option enabled,
provided that the channel names match and the source has an icon for that channel.

## «picons» utility

Allows you to download channel icons from the «epg.one» website and automatically converts the logo names into a format understandable for «TVLINK»
(for example: 7B7ADBFF.png).

The utility is console-based and is launched in the terminal. It is located in the «tvlink» directory, so you need to specify the full path to it.
For example:

    /storage/.config/tvlink/picons

Arguments Reference:

    /patch_to/tvlink/picons -h

Running the «picons» utility without arguments downloads and converts «transparent» icons.

The same action – downloading and converting icons – can also be performed in the «TVLINK» web interface on the «Sources» page.

<p align="center">
  <a href="/tvlink/channels/04.png"><img src="/tvlink/channels/04.png" width="480"/></a>
</p>

Select the necessary options and click «Create picons».

## Channel Numbers

In the «Num» column, you can specify channel numbers. You can specify a number for only one channel or not specify any at all.
In the playlist, channels will still be assigned numbers (in alphabetical order of channel names).
If a number is specified for at least one channel, the numbering will start from it. If no number is specified for any channel, the numbering will start from one.

## Channel Names

In the «Name» column, you can edit channel names. Changes take effect immediately after the row with the channel name loses focus.

## Channel Groups

In the «Group» column, you can change the group to which a channel belongs. Groups are selected from a list.

If you need to change the group for several channels at once:

1. Place checkmarks in the «Clean» fields next to the channels whose group you want to change.
2. Change the group for one of the checked channels. This will change the group for all selected channels.

<p align="center">
  <a href="/tvlink/channels/05.png"><img src="/tvlink/channels/05.png" width="480"/></a>
</p>

Clicking on the «Clean» label itself removes the checkmarks from all selected channels. This is in case you made a mistake in your selection.

## Channel Parameters

Icons in the «Control» column (from left to right):

+ «Info» – channel information and stream management
+ «Join» – joining channels and their streams
+ «Break» – disconnecting channels
+ «Delete» – deleting channels

### «Info»

If you need to disable or enable any channel streams, move the «Enable» switch to the desired position.

<p align="center">
  <a href="/tvlink/channels/06.png"><img src="/tvlink/channels/06.png" width="480"/></a>
</p>

In this table, the streams (links) are arranged in order of their priority.
That is, in the sequence in which «TVLINK» will switch between them if a failure occurs in the preceding stream.

### «Join»

«TVLINK» automatically merges channels with the same names. The case of characters and spaces in the channel name are ignored.
You can also merge channels manually. To do this, you need to select the channels (in the «Clean» column) that you would like
to add and click «Join» on the channel you want to merge them with.

<p align="center">
  <a href="/tvlink/channels/07.png"><img src="/tvlink/channels/07.png" width="480"/></a>
</p>

### «Break»

This procedure is the opposite of the previous one.

<p align="center">
  <a href="/tvlink/channels/08.png"><img src="/tvlink/channels/08.png" width="480"/></a>
</p>

### «Delete»

Deletes the channel from the «Channels» list. In doing so, the channel becomes available again in its source.

## Channel IDs

This column displays the unique identifier of the channel and contains a direct link to this channel.
This link can be pasted into a player (for example, VLC) to play the channel or simply record the stream in a browser.
To then play the recorded channel in a player, add the «.ts» extension to the file.

The «Play» icon next to the channel «ID» opens a simple web player.
This is for convenience when you need to test the channel. The web player does not support stream switching and may also not play some channels.

<p align="center">
  <a href="/tvlink/channels/09.png"><img src="/tvlink/channels/09.png" width="480"/></a>
</p>

---

«Delete channels» at the bottom of the page removes all channels from the «Channels» list.
