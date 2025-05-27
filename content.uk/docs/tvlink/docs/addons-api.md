---
title: API доповнень TVLINK
weight: 22
---

## Загальна інформація

Щоб створити своє доповнення, натисніть кнопку «Add addon» на сторінці «Sources».
У вікні «Add new addon» введіть назву майбутнього аддона.
Вона має бути написана латинськими літерами, без спеціальних символів (пробілів, тире тощо) та не може починатися з цифри.

<p align="center">
  <a href="/tvlink/addons/01.png"><img src="/tvlink/addons/01.png" width="480"/></a>
</p>

Натисніть «Save changes».

Якщо аддона з такою назвою (мається на увазі лише ім'я файла без розширення «.py»)
не існує в <a target='_blank' href="https://github.com/AlexELEC/TVLINK-ADDONS">репозиторії</a>,
буде створено порожній файл у каталозі «tvlink/scrapers». Наприклад, «tvlink/scrapers/Test.py».

## API доповнень

У доповненні обов'язково має бути підключений модуль «utils» (з TVLINK), який надає необхідні функції.

    # -*- coding: utf-8 -*-
    
    import os, sys
    from pathlib import Path
    
    root_dir = os.path.dirname(sys.argv[0])
    sys.path.append(root_dir)
    
    import utils
    from utils import DEF_BROWSER # User-Agent: "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:86.0) Firefox"

Також має бути оголошений клас «Scraper» з обов'язковими функціями «channels()» та «getLink()».

    class Scraper:
        def __init__(self): # Необов'язкова функція
            self.source  = Path(__file__).stem            # Назва доповнення
            self.link    = f'ext:{self.source}:'          # URL-префікс каналу
            self.headers = {'User-Agent': DEF_BROWSER}    # User-Agent для доповнення
    
        def getHeaders(self): # Необов'язкова функція
            return self.headers
    
        def Channels(self):
            LL = []
            RET_STATUS = False
            ...
            
            for cnLine in L:
                chTitle = cnLine.name                     # Назва каналу
                chLogo  = cnLine.icon                     # Логотип каналу
                chGroup = cnLine.group                    # Група каналу
                chID    = utils.title_to_crc32(chTitle)   # ID каналу
                chUrl   = f"{self.link}{cnLine.link}"     # Посилання на потік каналу
    
                LL.append((chID, chTitle, chGroup, chUrl, chLogo))
            
            if LL:
                # Завантаження каналів у базу даних TVLINK
                utils.ch_inputs_DB(self.source, LL)
                RET_STATUS = True
    
            # Повертає «True», якщо канали було завантажено до бази даних
            return RET_STATUS
    
        def getLink(self, url):
            ...
            return url

Усе інше (класи, функції, змінні тощо) ви можете писати на ваш розсуд.

### Функція Channels()

Викликається «TVLINK», коли потрібно створити "мапу каналів".
Наприклад, коли ви натискаєте кнопку «Update» джерела.

Повинна повертати «True» або «False» залежно від того, чи були канали завантажені до бази даних.

### Функція utils.title_to_crc32()

Функція приймає назву каналу (chTitle) як аргумент та повертає ID каналу (chID).

### Функція utils.ch_inputs_DB()

Функція приймає два аргументи:

1. ім'я джерела (повинно співпадати з ім'ям файла доповнення), self.source — у прикладі
2. список кортежів, у якому перераховані параметри каналу, LL — у прикладі

Кортеж має бути сформований у такому форматі та порядку:

    LL = ( (chID, chTitle, chGroup, chUrl, chLogo), )

+ chID - ідентифікатор каналу
+ chTitle - ім'я каналу
+ chGroup - група каналу
+ chUrl - URL каналу
+ chLogo - URL іконки каналу

З обов'язкового тут: chID, chTitle та chUrl.
По суті, вам із сайту (для якого ви пишете плагін) потрібно взяти як мінімум два значення – chTitle та chUrl.
Для отримання chID потрібно використовувати функцію utils.title_to_crc32(), яка поверне ідентифікатор каналу.
Решта змінних може містити порожній рядок.

«chUrl» (URL каналу) — має бути сформований у наступному форматі:

    ext:ім'я_аддона:http://посилання_на_канал

Наприклад, якщо аддон називається «Test», а посилання на потрібний канал — «http://tv.site.com/channel-1.html», то «chUrl» у нас буде виглядати так:

    ext:Test:http://tv.site.com/channel-1.html

Коли «TVLINK» вмикає канал за цим посиланням, він розуміє (за префіксом «ext:Test»),
що потрібно викликати функцію «getLink()» з аддона «Test» і передати їй як аргумент посилання «http://tv.site.com/channel-1.html».

### Функція getLink()

Функція приймає посилання на канал (chUrl) як аргумент та повертає посилання на реальну адресу потоку.

У простому випадку посилання на канал і потік може бути одне й те саме.
Тому вигляд функції може бути таким (що отримав — те й віддав).

    def getLink(self, lnk):
        return lnk

На практиці таке трапляється вкрай рідко. Зазвичай посилання на потік формуються на сайті динамічно при відкритті сторінки каналу, причому щоразу нові.
У цій функції ви повинні знайти таке посилання й повернути його «TVLINK», щоб він зміг його "програти".

### Модуль BeautifulSoup

Для парсингу сторінок сайту зручно використовувати модуль <a target='_blank' href="https://www.crummy.com/software/BeautifulSoup/">«BeautifulSoup»</a>.
Якщо ви бажаєте використовувати цей модуль у своєму плагіні, його потрібно підключити. Робиться це так:

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
