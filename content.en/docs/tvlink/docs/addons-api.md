---
title: TVLINK Add-ons API
weight: 22
---

## General Information

To create your own add-on, click the «Add addon» button on the «Sources» page.
In the «Add new addon» window, enter the name of the future add-on.
It must be written in Latin letters, without special symbols (spaces, hyphens, etc.) and cannot start with a digit.

<p align="center">
  <a href="/tvlink/addons/01.png"><img src="/tvlink/addons/01.png" width="480"/></a>
</p>

Click «Save changes».

If an add-on with such a name (meaning only the file name without the «.py» extension)
does not exist in the <a target='_blank' href="https://github.com/AlexELEC/TVLINK-ADDONS">repository</a>,
an empty file will be created in the «tvlink/scrapers» directory. For example, «tvlink/scrapers/Test.py».

## Add-ons API

The «utils» module (from TVLINK), which provides the necessary functions, must be connected in the add-on.

    # -*- coding: utf-8 -*-
    
    import os, sys
    from pathlib import Path
    
    root_dir = os.path.dirname(sys.argv[0])
    sys.path.append(root_dir)
    
    import utils
    from utils import DEF_BROWSER # User-Agent: "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:86.0) Firefox"

Also, a «Scraper» class with the mandatory functions «channels()» and «getLink()» must be declared.

    class Scraper:
        def __init__(self): # Optional function
            self.source  = Path(__file__).stem            # Add-on name
            self.link    = f'ext:{self.source}:'          # Channel URL prefix
            self.headers = {'User-Agent': DEF_BROWSER}    # User-Agent for the add-on
    
        def getHeaders(self): # Optional function
            return self.headers
    
        def Channels(self):
            LL = []
            RET_STATUS = False
            ...
            
            for cnLine in L:
                chTitle = cnLine.name                     # Channel name
                chLogo  = cnLine.icon                     # Channel logo
                chGroup = cnLine.group                    # Channel group
                chID    = utils.title_to_crc32(chTitle)   # Channel ID
                chUrl   = f"{self.link}{cnLine.link}"     # Channel stream link   
    
                LL.append((chID, chTitle, chGroup, chUrl, chLogo))
            
            if LL:
                # Loading channels into the TVLINK database
                utils.ch_inputs_DB(self.source, LL)
                RET_STATUS = True
    
            # Returns «True» if the channels were loaded into the database
            return RET_STATUS
    
        def getLink(self, url):
            ...
            return url

Everything else (classes, functions, variables, etc.) you can write at your discretion.

### Function Channels()

Called by «TVLINK» when it is necessary to create a "channel map".
For example, when you click the «Update» button of a source.

Must return «True» or «False» depending on whether the channels were loaded into the database.

### Function utils.title_to_crc32()

The function takes the channel name (chTitle) as an argument and returns the channel ID (chID).

### Function utils.ch_inputs_DB()

The function takes two arguments:

1. the source name (must match the add-on file name), self.source — in the example
2. a list of tuples, which enumerates the channel parameters, LL — in the example

The tuple must be formed in the following format and order:

    LL = ( (chID, chTitle, chGroup, chUrl, chLogo), )

+ chID - channel identifier
+ chTitle - channel name
+ chGroup - channel group
+ chUrl - channel URL
+ chLogo - channel icon URL

Of the mandatory ones here: chID, chTitle, and chUrl.
Essentially, you need to take at least two values from the website (for which you are writing the plugin) – chTitle and chUrl.
To obtain chID, you need to use the utils.title_to_crc32() function, which will return the channel identifier.
The remaining variables can contain an empty string.

«chUrl» (channel URL) — must be formed in the following format:

    ext:add-on_name:http://channel_link

For example, if the add-on is called «Test», and the link to the desired channel is «http://tv.site.com/channel-1.html», then «chUrl» will look like this:

    ext:Test:http://tv.site.com/channel-1.html

When «TVLINK» turns on a channel using this link, it understands (by the «ext:Test» prefix) that it needs to call the «getLink()» function
from the «Test» add-on and pass the link «http://tv.site.com/channel-1.html» to it as an argument.

### Function getLink()

The function takes a link to the channel (chUrl) as an argument and returns a link to the actual stream address.

In a simple case, the link to the channel and the stream can be the same.
Therefore, the function can look like this (what was received is what was returned).

    def getLink(self, lnk):
        return lnk

In practice, this happens extremely rarely. Usually, stream links are generated dynamically on the website when the channel page is opened, and they are new each time.
In this function, you must find such a link and return it to «TVLINK» so that it can "play" it.

### BeautifulSoup Module

It is convenient to use the <a target='_blank' href="https://www.crummy.com/software/BeautifulSoup/">«BeautifulSoup»</a> module for parsing website pages.
If you wish to use this module in your plugin, it needs to be connected. This is done as follows:

    # -*- coding: utf-8 -*-
    
    import os, sys
    
    root_dir = os.path.dirname(sys.argv[0])
    libs_dir = os.path.join(root_dir, 'libs')
    ssv_file = os.path.join(libs_dir, 'soupsieve.whl')
    bs4_file = os.path.join(libs_dir, 'beautifulsoup.whl')
    
    sys.path.append(root_dir)
    sys.path.append(libs_dir)
    sys.path.insert(0, ssv_file)
    sys.path.insert(0, bs4_file)
    
    from bs4 import BeautifulSoup
