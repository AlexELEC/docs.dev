---
title: Entware
weight: 12
---

## Entware

{{% hint info %}}
Репозиторій <a target='_blank' href="https://entware.net/about.html">«Entware»</a> надає можливість легко встановлювати додаткове програмне забезпечення на системи «LibreELEC/CoreELEC».

Список доступних пакетів можна переглянути <a target='_blank' href="https://bin.entware.net/x64-k3.2/Packages.html">тут</a>.
{{% /hint %}}


### Приклад встановлення «BitTorrent» клієнта «Transmission»

Встановлення «Entware»:

    installentware

В кінці з'явиться запитання:

    Would you like to reboot now to finish installation (recommended) [y/N]?

Наразі відповідаємо «Ні», просто натисніть «Enter».

Встановлення <a target='_blank' href="https://transmissionbt.com/">«Transmission»</a>:

    opkg install transmission-web

Перезавантаження системи:

    reboot

У браузері введіть адресу «http://your-ip-address:9091» і користуйтеся.

<p align="center">
  <a href="/alexelec/entware/01.png"><img src="/alexelec/entware/01.png" width="480"/></a>
</p>

Якщо потрібно видалити «Entware»:

    systemctl stop entware
    rm -fr /opt/*
    reboot
