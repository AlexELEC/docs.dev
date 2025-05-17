---
title: User Profiles
weight: 15
---

## User Profiles

{{% hint info %}}
Profile settings need to be configured after you have added channels to «TVLINK» (channel mapping).
{{% /hint %}}

User profiles allow you to have different sets of channels and groups for different clients.
Channels and groups in profiles are taken from the main set of channels on the «Channels» page (main profile),
so you first need to add all the channels that you might need in profiles to «Channels».

Also, when creating a profile, you can set the IP address for the streams and playlists of this profile and an authentication token, if necessary.

Click the «Add user» button in the «User Profiles» section and fill out the «Add user profile» form.

+ «User» — The client's name. It must consist of Latin letters, not contain special characters (spaces, hyphens, etc.), and cannot start with a digit.
+ «Playlist IP» — The address that will be used for the playlists and streams of this profile.
+ «Token for playlist/streams» — The token that will be used for the playlists and streams of this profile if the «Authentication Token» option is activated.
If this field is left empty, a token will be created automatically.
+ «Comment» — Any comment.


{{% hint info %}}
Apart from the «User» field, filling in all other fields is optional.
{{% /hint %}}

<p align="center">
  <a href="/tvlink/profiles/01.png"><img src="/tvlink/profiles/01.png" width="480"/></a>
</p>

After confirming the changes («Save changes»), the profile name («User») becomes a link.
Clicking on this link opens the group and channel settings of the profile.

<p align="center">
  <a href="/tvlink/profiles/02.png"><img src="/tvlink/profiles/02.png" width="480"/></a>
</p>
<p align="center">
  <a href="/tvlink/profiles/03.png"><img src="/tvlink/profiles/03.png" width="480"/></a>
</p>

You can disable groups and individual channels that should not be in this profile, or enable the necessary ones.

The «Settings» icon next to the profile name allows you to change all options (Playlist IP, Token, Comment).

<p align="center">
  <a href="/tvlink/profiles/04.png"><img src="/tvlink/profiles/04.png" width="480"/></a>
</p>

{{% hint info %}}
After any changes to the «Tokens» settings, you need to apply the settings («Apply Settings» at the bottom of the page) or restart the application.
{{% /hint %}}

{{% hint warning %}}
If you have the «Create static playlist» option enabled, then after any changes to the «Tokens» or Playlist IP settings,
do not forget to update the static playlists (click «Create static playlist» on the «Sources» page).
{{% /hint %}}

The «Delete» icon deletes the profile.

In the «Playlist URL» column, the links to the profile's playlist are displayed in the following format:

    http://<ip-address>:<port>/<token>/playlist/<user>

+ token – if «Authentication Token» is activated
+ user – profile name

For «PVR TVLINK Client», it is sufficient to specify the profile name and token in the settings.
