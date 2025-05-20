---
title: PVR TVLINK клієнт
weight: 20
---

## PVR TVLINK клієнт для Kodi

Як клієнт (IPTV-програвач) для «TVLINK» найкраще підходить «PVR TVLINK Client» для «Kodi».
Лише цей клієнт надасть вам усі можливості сервера «TVLINK».
Серед них, наприклад, непомітне для користувача перемикання потоків (у разі збоїв трансляції) одного й того самого каналу з різними форматами аудіо та відео.
Клієнт підтримує Timeshift (паузу/перемотування), IPTV-архіви та EPG.

<p align="center">
  <a href="/tvlink/pvr-client/01.png"><img src="/tvlink/pvr-client/01.png" width="480"/></a>
</p>

<a target='_blank' href="https://github.com/AlexELEC/pvr.tvlink">Код клієнта</a> базується на <a target='_blank' href="https://github.com/kodi-pvr/pvr.iptvsimple">«PVR IPTV Simple»</a>,
але розроблений так, щоб відповідати всім вимогам «TVLINK».
Наприклад, клієнт ніколи не розриватиме з'єднання з сервером «TVLINK» самостійно.
Це відбудеться лише тоді, коли користувач перемкне канал або зупинить трансляцію каналу.

{{% hint warning %}}
Для роботи «PVR TVLINK Client» потрібна модифікована версія «Kodi»; він не працюватиме з оригінальною версією «Kodi».
{{% /hint %}}

## Налаштування

### «General»

<p align="center">
  <a href="/tvlink/pvr-client/02.png"><img src="/tvlink/pvr-client/02.png" width="480"/></a>
</p>

+ «TVLINK IP-address» – IP-адреса сервера «TVLINK».
+ «TVLINK port» – порт сервера «TVLINK».
+ «TVLINK profile» – профіль користувача на сервері «TVLINK». Якщо не вказано, використовується основний профіль (main).
+ «Auth. Token» – токен авторизації, якщо потрібен.

+ «FFmpeg playlist» – увімкніть, якщо ви хочете отримувати трансляції, які оброблятимуться ffmpeg-модулем «TVLINK».

### «Streams»

<p align="center">
  <a href="/tvlink/pvr-client/03.png"><img src="/tvlink/pvr-client/03.png" width="480"/></a>
</p>

+ «TVLINK connection timeout» – тайм-аут з’єднання клієнта з сервером «TVLINK» для отримання списку каналів. Ця опція не впливає на трансляції.
+ «Buffering streams» – якщо активовано, клієнт буде додатково буферизувати потоки (засобами Kodi).
+ «FFmpegDirect for Timeshift» – вмикає функцію Timeshift через доповнення «Inputstream FFmpeg Direct».

+ «FFmpegDirect for Catchup» – вмикає функцію Catchup через доповнення «Inputstream FFmpeg Direct».

Дві останні опції («FFmpegDirect for ...») будуть працювати тільки якщо ви встановите доповнення <a target='_blank' href="https://kodi.wiki/view/Add-on:Inputstream_FFmpeg_Direct">«Inputstream FFmpeg Direct»</a>.
В іншому випадку кліент їх буде ігнорувати.

«Timeshift» працює тільки коли ввімкненна опція «FFmpegDirect for Timeshift». Для роботи IPTV-архівів (Catchup) – «FFmpegDirect for Catchup» не обовязкова.

{{% hint info %}}
Доповнення «Inputstream FFmpeg Direct» не корректно (на данний час) працює на деяких архітектурах, наприклад Intel.
Якщо ви активуете «FFmpegDirect for Timeshift» – у вас перестане працювати автоматична зміна потоків в каналі.
Доповнення «Inputstream FFmpeg Direct», через яке будуть проходити потоки, не вміє автоматично змінювати параметри потоку.
{{% /hint %}}

---

Всі інші налаштування такі самі як і в «PVR IPTV Simple» клієнта.

<p align="center">
  <a href="/tvlink/pvr-client/04.png"><img src="/tvlink/pvr-client/04.png" width="480"/></a>
</p>
