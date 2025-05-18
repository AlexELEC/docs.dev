---
title: Channel Groups
weight: 17
---

## Channel Groups

{{% hint info %}}
This information pertains to the settings on the «Groups» page.
{{% /hint %}}

### Groups

<p align="center">
  <a href="/tvlink/groups/01.png"><img src="/tvlink/groups/01.png" width="480"/></a>
</p>

Buttons:

+ «Create new group» – allows you to create a new group. The new group becomes available on the «Channels» page.
+ «Clean all groups» – deletes all groups without exception.

Table:

+ «Title» – the group name. If you change the group name, the group name of all channels belonging to this group will also change (this refers to the «Channels» page).
If another group is given the same name, these two groups will be merged into one.
+ «Enabled» – if disabled, all channels of this group will be removed from the «Channels» page, and when updating (or adding new) sources,
channels belonging to this group will not be added to the «TVLINK» channel list. If enabled (after being disabled) and the source(s) are updated, the channels of this group will return to «Channels».
+ «Control» – the blue icon allows you to set «Aliases» for the group. The red icon deletes the group.

Group aliases are set via a comma. The case of characters in aliases does not matter. You can write: “Films”, “FILMS”, or “FiLmS”.
If an alias is specified for a group, then during channel mapping, the source group will be replaced with the original one in the «Channels» list.

<p align="center">
  <a href="/tvlink/groups/02.png"><img src="/tvlink/groups/02.png" width="480"/></a>
</p>

It is not a complete match with the template (alias) that is checked, but rather the inclusion of a word in the template.
For example, if you set the alias “Films and series” for the group “Films”, the following groups will fall into the “Films” group (case-insensitive): “Films and series”, “Series”, and of course, “Films”.

You can only delete a group if no channel on the «Channels» page belongs to this group.
Otherwise, «TVLINK» will not allow you to do this. You can, for example, first disable the group and then delete it if there are channels in the group.

### Sorting Groups

«Sort groups» at the bottom of the page will open these settings.

<p align="center">
  <a href="/tvlink/groups/03.png"><img src="/tvlink/groups/03.png" width="480"/></a>
</p>

The sorting order is set by a number. The smaller the number, the higher the group is in the list.
On the sorting page, all active (not disabled) groups to which at least one channel has been added are displayed, regardless of whether this channel is currently on the «Channels» page.
Channel numbering (if present) takes priority over group sorting. To see how the list of channels and groups will look after their sorting/numbering, sort the channels by «Group» on the «Channels» page.
This exact order of channels will be in the playlist. The sorting itself (by numbers, names, groups) on the «Channels» page does not affect the playlist; it is only for the convenience of editing channels.
