---
title: Огляд
weight: 10
---

## Завантаження образів та оновлення систем

+ <a target='_blank' href="https://github.com/AlexELEC/LibreELEC-21/releases">LibreELEC</a>
+ <a target='_blank' href="https://github.com/AlexELEC/CoreELEC-21/releases">CoreELEC</a>

## Програмний код

+ <a target='_blank' href="https://github.com/AlexELEC/LibreELEC-21">LibreELEC</a>
+ <a target='_blank' href="https://github.com/AlexELEC/CoreELEC-21">CoreELEC</a>

## Відмінності від оригінальних версій

+ SSH (логін/пароль) за замовчуванням: *root/mcpc*
+ З налаштувань «LibreELEC/CoreELEC» видалено функцію автоматичного оновлення системи.
+ В систему інтегровано файловий менеджер «Midnight Commander» та утиліту «htop».
+ Додано сервіс «hid-remote» для налаштування HID-пультів дистанційного керування.
+ Додано пакети (залежності) для роботи «TVLINK IPTV server».
+ «TVLINK IPTV server» можна завантажити, активувати або відключити в налаштуваннях системи.
+ «PVR TVLINK Client» інтегровано в систему.

**Для «Kodi»:**

+ Додано PVR-API для «PVR TVLINK Client».
+ Оптимізовано швидкість перемикання каналів.
+ Додано можливість автоматичної зміни параметрів аудіо- та відеопотоків, що необхідно для «TVLINK», коли він змінює потік для того самого каналу.
+ Додано репозиторій <a target='_blank' href="https://github.com/AlexELEC/repo-21/tree/master/Omega/common">«AlexELEC Common Add-ons»</a>,
з якого можна встановити доповнення: «TVLINK Simple Control», «Keyboard Layout» та інші.

**LibreELEC**

В цю систему (в CoreELEC ця можливість є за замовчуванням) додано можливість встановлювати пакети з репозиторію <a target='_blank' href="https://wiki.coreelec.org/coreelec:entware">«Entware»</a>.

**CoreELEC**

Файл конфігурації пульта дистанційного керування (*remote.conf*) може знаходитися в каталозі «/storage/.config/amremote» або «/storage/.config».
Останній має пріоритет.
