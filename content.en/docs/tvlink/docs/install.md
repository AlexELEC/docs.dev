---
title: Installation
weight: 11
---

## Installation & Update

{{% hint info %}}
<a target='_blank' href="https://github.com/AlexELEC/TVLINK-Releases/releases">«TVLINK» releases</a> are compiled only for «Linux».
{{% /hint %}}

The program uses «<a target='_blank' href="https://streamlink.github.io/">Streamlink</a>» Python modules,
therefore the following must be installed on the system:

+ **Python**. The required «Python» version is specified in the release title.
+ «Runtime» dependencies for «Streamlink», which you can see <a target='_blank' href="https://streamlink.github.io/install.html#dependencies">here</a>.

{{% hint warning %}}
You do not need to install «Streamlink» itself, and it is not recommended. This will cause conflicts
in the program's operation. The «Streamlink» modules are part of «TVLINK».
{{% /hint %}}

{{< tabs >}}

{{% tab "LibreELEC/CoreELEC" %}}

## LibreELEC/CoreELEC

{{% hint info %}}
Modified systems (ae-fork) are implied, in which all the necessary dependencies are already present.
The program cannot function in the original ELEC systems.
{{% /hint %}}

In the system settings ("LibreELEC/CoreELEC" -> "TV services" -> "TVLINK server"), click "Enable TVLINK".
The program will be installed and started automatically.

<p align="center">
  <img src="/tvlink/install/install-libre.png" />
</p>

{{% /tab %}}

{{% tab "Ubuntu/Debian/Armbian" %}}

## Ubuntu/Debian/Armbian

{{% hint info %}}
Remember that the corresponding version of «Python» must be installed on the system. The «Python» version is specified in the filename.
For example: TVLINK-4.2.4-x86_64-**python_3.12**-Ubuntu.deb.
{{% /hint %}}

For these **x86-64** architecture systems, you can download and install «TVLINK» using a *deb* package.
Download the required file and enter the commands in the terminal:

    apt install ./TVLINK-4.2.4-x86_64-python_3.12-Ubuntu.deb
    systemctl start tvlink
    systemctl enable tvlink

+ ### Armbian (aarch64)

You can also install «TVLINK» from an archive.

{{% hint info %}}
For example, «Armbian Minimal/IOT Distro: Debian 12 (Bookworm)» for <a target='_blank' href="https://www.armbian.com/amlogic-s9xx-tv-box/">Amlogic S912</a>.
{{% /hint %}}

«TVLINK» uses the "ping" utility. We will install it, as well as some utilities that we will need.

    apt install -y mc tar bzip2 wget iputils-ping

Let's install the dependencies for «Streamlink» (python3-streamlink). This can be done with a single command:

    apt install -y $(apt-cache depends python3-streamlink | grep Depends | sed "s/.*ends:\ //; s/<.*>//" | tr '\n' ' ')

{{% hint info %}}
Here, the command «apt-cache depends python3-streamlink» outputs information about the dependencies of the «Streamlink» modules,
and «grep, sed, tr» create a list from it that is passed to «apt install».
{{% /hint %}}

Let's download and install «TVLINK».

    mkdir -p /opt/tvlink
    cd /opt
    wget https://github.com/AlexELEC/TVLINK-Releases/releases/download/4.2.4/TVLINK-4.2.4-aarch64-python_3.11.tar.bz2 -O TVLINK.tar.bz2
    tar -jxf TVLINK.tar.bz2 --directory /opt/tvlink
    rm -f TVLINK.tar.bz2

Let's run «TVLINK» to check:

    root@armbian:/# /opt/tvlink/tvlink

    — Starting TVLINK (version: 4.2.4) on 127.0.0.1:2020 / 192.168.1.33:2020 —

It is recommended to go to the web interface (for example: http://192.168.1.33:2020), add channels, and check their operation.
Errors related to dependencies can only be seen in the terminal; they are not recorded in the «TVLINK» log.

If everything is fine, terminate «TVLINK» (Ctrl+C) and add it to the system autostart.

    wget https://github.com/AlexELEC/TVLINK-Releases/raw/refs/heads/main/scripts/Ubuntu/tvlink.service -O /etc/systemd/system/tvlink.service
    
    systemctl enable tvlink
    systemctl start tvlink

{{% /tab %}}

{{% tab "OpenWRT (х86-64)" %}}

## OpenWRT (х86-64)

{{% hint info %}}
A simple way to install the OpenWRT system for the x86-64 architecture is described here.
{{% /hint %}}

{{% hint info %}}
The «OpenWRT» version for which the program is compiled is specified in the release description.
{{% /hint %}}

Let's update the package repositories and install the dependencies for the «Streamlink» module, which is included in «TVLINK».
Enter the following commands sequentially in the terminal:

    opkg update
    opkg install python3 python3-certifi python3-chardet python3-cryptodome python3-pip python3-requests python3-six python3-lxml tar wget
    python -m pip install --upgrade pip
    pip install pycountry isodate pysocks

Let's download and install «TVLINK» itself.

    wget https://github.com/AlexELEC/TVLINK-Releases/releases/download/4.2.4/TVLINK-4.2.4-x86_64-python_3.11-Openwrt.tar.bz2 -O TVLINK.tar.bz2
    mkdir -p /opt/tvlink
    tar -jxf TVLINK.tar.bz2 -C /opt/tvlink
    rm -f TVLINK.tar.bz2

Let's check if the program works.

    /opt/tvlink/tvlink

    — Starting TVLINK (version: 4.2.4) on 127.0.0.1:2020 / 192.168.1.1:2020 —

It is recommended to go to the web interface (for example: http://192.168.1.1:2020), add channels, and check their operation.
Errors related to dependencies can only be seen in the terminal; they are not recorded in the «TVLINK» log.

If «TVLINK» works without errors, close it (Ctrl+C). Download and add the service to autostart.

    cd /etc/init.d
    wget https://github.com/AlexELEC/TVLINK-Releases/raw/refs/heads/main/scripts/Openwrt/tvlink -O /etc/init.d/tvlink && chmod +x /etc/init.d/tvlink
    
    service tvlink enable
    service tvlink start

{{% /tab %}}

{{< /tabs >}}

## Program Update

[Read here](/docs/tvlink/docs/status/#program-update) on how to update the program.
