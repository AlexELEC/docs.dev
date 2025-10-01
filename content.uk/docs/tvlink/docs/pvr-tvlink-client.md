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

### «Streams»

<p align="center">
  <a href="/tvlink/pvr-client/03.png"><img src="/tvlink/pvr-client/03.png" width="480"/></a>
</p>

+ «TVLINK connection timeout» – тайм-аут з’єднання клієнта з сервером «TVLINK» для отримання списку каналів. Ця опція не впливає на трансляції.

+ «Buffering streams» – якщо активовано, клієнт буде додатково буферизувати потоки (засобами Kodi).

+ «Use Inputstream FFmpeg Direct» – увімкнення цього параметра активує функції Timeshift та Catchup за допомогою доповнення «Inputstream FFmpeg Direct».

{{% hint info %}}
Ця остання опція («Use Inputstream FFmpeg Direct») працюватиме лише за умови, що ви активуєте доповнення «Inputstream FFmpeg Direct».
В іншому випадку клієнт ігноруватиме ці функції.

Доповнення «Inputstream FFmpeg Direct» спеціально змінено для роботи з «TVLINK» і вбудовано в систему.
Якщо ви оновите його на оригінальну версію, воно втратить свою функціональність щодо «TVLINK».
{{% /hint %}}

Всі інші налаштування такі самі, як і в клієнта «PVR IPTV Simple».

<p align="center">
  <a href="/tvlink/pvr-client/04.png"><img src="/tvlink/pvr-client/04.png" width="480"/></a>
</p>

## Функції «TimeShift» та «Catchup»

Ці функції дозволяють перемотувати прямий ефір назад (а потім і вперед), якщо ваш IPTV-провайдер надає послугу «IPTV-архіви».

+ «TimeShift» — це перемотування безпосередньо під час перегляду телеканалу. Наприклад, ви запустили канал, де фільм уже йде 30 хвилин.
Ви натискаєте кнопку «вниз» до потрібного моменту та дивитесь фільм спочатку.

+ «Catchup» — це запуск телепередачі (яка вже минула) з «EPG».

{{% hint info %}}
«TimeShift» працює тільки тоді, коли увімкнена опція «Use Inputstream FFmpeg Direct». Для роботи IPTV-архівів (Catchup) опція «Use Inputstream FFmpeg Direct» не є обов'язковою.
{{% /hint %}}
