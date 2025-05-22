---
title: HID Remote Control Configuration
weight: 11
---

## HID Remote Control Configuration in «LibreELEC/CoreELEC» (ae-fork) Systems

{{% hint info %}}
A "Human Interface Device" (HID) remote control refers to a remote control that functions as a standard keyboard or mouse input device.
It allows users to interact with a computer or other device by emulating standard input actions like keyboard key presses or mouse clicks. 
{{% /hint %}}

HID remote controls have some advantages over IR remotes. Firstly, you do not need to point the remote at the signal receiver.
Secondly, HID remotes (as they emulate a keyboard) support the «long press» function. This means that one button can be programmed for two different actions.

This instruction concerns «G20S PRO» (USB 2.4G) and «G20S PRO BT» (USB 2.4G + Bluetooth) remote controls, which do not differ in appearance but have different button codes.
We will only use the «USB 2.4G» interface.

The «HID-Remote» service uses the <a target='_blank' href="https://github.com/AlexELEC/hid_mapper/blob/master/README">«hid_mapper»</a> utility.

<p align="center">
  <a href="/alexelec/hid-remote/01.png"><img src="/alexelec/hid-remote/01.png" width="480"/></a>
</p>

{{% hint warning %}}
Attention! After the system is turned off, the remote goes to sleep mode.
This saves battery power, but upon the next power-on, you need to press any button several times for the remote to wake up.

If you press the keyboard/mouse switch button, this will change the button codes that the remote control sends.
Accordingly, some buttons may stop working.
{{% /hint %}}

## «HID-Remote» Service

All settings are located in the «/storage/.config/hid_remote/» directory. Hereafter, all file paths will be relative to this directory.

For «G20S PRO/G20S PRO BT» remotes (and for some others), a configuration already exists in the system.
You only need to replace the contents of the «remote.map» file with the contents of the «sample/Gi20sPRO.map» or «sample/Gi20sPRO-BT.map»
file (for G20S PRO BT) and specify the values for the «MANUFACTURER» and «PRODUCT» variables in the «device.conf» file.
The corresponding values for these variables are also located in the mentioned «map» files. After that, you will only need to enable the «HID-Remote» service.

<p align="center">
  <a href="/alexelec/hid-remote/02.png"><img src="/alexelec/hid-remote/02.png" width="480"/></a>
</p>

{{% hint info %}}
When the «HID-Remote» service is activated, the «Eventlircd» service will be disabled. This is done to prevent the double triggering effect of the remote control buttons.
{{% /hint %}}

## Manual Configuration for the «HID-Remote» Service

If you have a remote of another model, you do not need to configure all of its buttons.
Usually, only two or three buttons may not work because they send the press code of several keys at once.
This may also be necessary if you want to remap the action of a specific button.

Stop the «Kodi» and «Eventlircd» services by executing the following commands in the terminal:

    systemctl stop kodi
    systemctl stop eventlircd

In the «device.conf» file, you need to set the values for the «MANUFACTURER» and «PRODUCT» variables for your HID device.
To do this, execute the command (there is a hint in the device.conf file):

    hid-remote --list-devices --lookup-id

If you do not have other input devices connected (besides the remote), you will see something like this:

<p align="center">
  <a href="/alexelec/hid-remote/03.png"><img src="/alexelec/hid-remote/03.png" width="480"/></a>
</p>

Here, two devices with the same «Manufacturer/Product name» values are shown — this is because the remote is identified as both a keyboard and a mouse.

Enter the obtained values into the «device.conf» file.

    MANUFACTURER="1915"
    PRODUCT="1025"

Now, let's configure the «remote.map» file by mapping the remote button codes to the desired keyboard keys.

The format of the «remote.map» file is:

    Remote_Button_Code:Keyboard_Key_Name

For example:

    024100:KEY_ENTER

Let's determine the code of the required remote button. To do this, execute the following command:

    hid-remote --lookup-id --learn --manufacturer <MANUFACTURER> --product <PRODUCT>

Here, you need to substitute the values of the «MANUFACTURER» and «PRODUCT» variables that we obtained earlier.
Press the desired button on the remote and get its code.

The example below shows the code for the «OK» button.

<p align="center">
  <a href="/alexelec/hid-remote/04.png"><img src="/alexelec/hid-remote/04.png" width="480"/></a>
</p>

    02 41 00 - button press code
    02 00 00 - button release code (it will be the same for almost all buttons)

We need the first code. Write it to the «remote.map» file without spaces.

In the «sample/keys.sample» file, you will find all the necessary keyboard key names.

After editing the «device.conf» and «remote.map» files, activate the «HID-Remote» service in the system settings.

## The «Power» Button

Usually, the «Power» button on the remote control functions the same way as the «Power» button on the computer case: it immediately turns off the computer.
If this behavior does not suit you, and you wish for this button to bring up the «Shoutdown» menu (for example, for setting a timer), follow these steps:

1. Copy the file «/etc/systemd/logind.conf» to the directory «/storage/.config/logind.conf.d».

2. Edit the following line in the copied file:

{{% hint %}}
    HandlePowerKey=ignore
{{% /hint %}}

To make the changes take effect, you need to reboot the system.
