---
title: Electronic Program Guide
weight: 14
---

## Electronic Program Guide

{{% hint info %}}
EPG configuration needs to be performed after you have added channels in «TVLINK» (channel mapping).
{{% /hint %}}

You can use the EPG sources that are already present in the program (EPG Static sources),
or create your own (EPG Custom sources). Activate the required switch.

<p align="center">
  <a href="/tvlink/epg/01.png"><img src="/tvlink/epg/01.png" width="480"/></a>
</p>

To create a custom source, click the «Add EPG» button and complete the «Add new EPG» form.

<p align="center">
  <a href="/tvlink/epg/02.png"><img src="/tvlink/epg/02.png" width="480"/></a>
</p>

+ «EPG name» — any name of your choice. It must consist of Latin letters, without special characters (spaces, hyphens, etc.) and cannot start with a digit.
+ «EPG url» — the address of the XMLTV file. It can be archived (.tar.gz) or not archived (.xmltv).

Click «Save changes» to save the settings.

<p align="center">
  <a href="/tvlink/epg/03.png"><img src="/tvlink/epg/03.png" width="480"/></a>
</p>

### Options

+ «Name» — the name of the source and a link (when the source is active and updated) to edit (match) channels for this source.
+ «Enable» — enabling/disabling the source.
+ «Prio» — priority. If several sources are active, «TVLINK» will search for matches between channels and programs in the order of source priority.
Items not found in the first source will be searched for in the second, and so on.
+ «File date» — if the XMLTV source provides such information, the creation date of the source's XMLTV file will be indicated here.
If such information is not provided, the date of the last file download will be indicated here.
+ «Update» — information about the last channel matching and program creation, as well as the «Update» button.
Its actions are limited to downloading and automatically matching channel names with the program.
This allows you to manually match those channels that «TVLINK» could not match automatically, or change the automatic matching if needed.
+ «Channels» — the total number of channel names in the source is displayed here.
This is for informational purposes only, as not all channels listed in the source necessarily include program data.

### Buttons

+ «Create EPG» — generates the program. The XMLTV file will be available at: «http://ip-address:port/xmltv»
+ «Clean manual EPG mapping» — clears all the mappings you have done manually.

After you have clicked the button in the «Update» column, you can follow the link from the «Name» column and match the channels that «TVLINK» could not match,
or change the matching of channels that do not meet your requirements.

<p align="center">
  <a href="/tvlink/epg/04.png"><img src="/tvlink/epg/04.png" width="480"/></a>
</p>

+ «Auto EPG mapping» — this column displays the names of channels from the XMLTV source that «TVLINK» has automatically matched.
+ «Manual EPG mapping» — this is where you can manually match channels.

<p align="center">
  <a href="/tvlink/epg/05.png"><img src="/tvlink/epg/05.png" width="480"/></a>
</p>

After sorting the table by the «Auto EPG mapping» column, we will get all the channels that were not automatically matched at the top of the list (for convenience).

Since the drop-down list of the «Manual EPG mapping» column contains all the channel names from the EPG source, finding the required one is quite difficult.
To simplify the task, you need to enter the first letters of the channel name and the list will move to the desired position.

After setting up, return to the «Sources» page and click the «Create EPG» button.

In the «EPG Static sources», you have the option to change the URL address if needed. To do this, click the «Edit» icon next to the source name.

The update frequency of EPG sources is set on the «Settings» page in the «EPG settings» section.
