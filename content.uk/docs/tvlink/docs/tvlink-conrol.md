---
title: TVLINK Simple Control
weight: 21
---

## Доповнення «TVLINK Simple Control» для Kodi

Доповнення можна встановити з репозиторію <a target='_blank' href="https://github.com/AlexELEC/repo-21/tree/master/Omega/common">«AlexELEC Common Add-ons»</a>,
яке є в системах «LibreELEC/CoreELEC (ae-fork)».

<p align="center">
  <a href="/tvlink/tvlink-control/01.png"><img src="/tvlink/tvlink-control/01.png" width="480"/></a>
</p>

Дозволяє контролювати потоки каналу (вмикати/вимикати) та показує (виділяє жовтим кольором) посилання на потік, який транслюється в цей момент.

<p align="center">
  <a href="/tvlink/tvlink-control/02.png"><img src="/tvlink/tvlink-control/02.png" width="480"/></a>
</p>

Також надає можливість:

+ послідовно перемикати потоки каналу;
+ оновлювати джерела каналів «TVLINK»;
+ показувати інформацію про підключених до «TVLINK» клієнтів;
+ показувати інформацію про використання оперативної пам’яті та сокетів.

<p align="center">
  <a href="/tvlink/tvlink-control/03.png"><img src="/tvlink/tvlink-control/03.png" width="480"/></a>
</p>

## Налаштування

<p align="center">
  <a href="/tvlink/tvlink-control/04.png"><img src="/tvlink/tvlink-control/04.png" width="480"/></a>
</p>

+ «IP-address TVLINK» – IP-адреса сервера «TVLINK»
+ «Port TVLINK» – порт сервера «TVLINK»

{{% hint info %}}
Якщо «IP-address TVLINK» не вказано, «TVLINK Simple Control» використовує адресу «127.0.0.1».
{{% /hint %}}

У модифікованих (ae-fork) ELEC-системах доповнення викликається довгим натисканням кнопки «і» (info) на клавіатурі.
Для пультів дистанційного керування в цих системах зроблені такі налаштування файлу «keyboard.xml» у Kodi.

    <FullscreenLiveTV>
        <keyboard>
            …
            <i mod="longpress">RunAddon(script.tvlink.conrol)</i>
        </keyboard>
    </FullscreenLiveTV>
