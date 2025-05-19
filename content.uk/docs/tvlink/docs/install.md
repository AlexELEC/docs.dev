---
title: Встановлення програми
weight: 11
---

## Встановлення

{{% hint info %}}
<a target='_blank' href="https://github.com/AlexELEC/TVLINK-Releases/releases">Релізи</a> «TVLINK» компілюються тільки для «Linux».
{{% /hint %}}

Програма використовує Python-модулі «<a target='_blank' href="https://streamlink.github.io/">Streamlink</a>»,
тому в системі повинні бути встановлені:

+ **Python відповідної версії**. Потрібна версія «Python» вказана в назві релізу.
+ «Runtime» залежності для «Streamlink», які ви можете бачити <a target='_blank' href="https://streamlink.github.io/install.html#dependencies">тут</a>.

{{% hint warning %}}
Сам «Streamlink» встановлювати не потрібно і не бажано. Це викличне конфлікти в роботі програми.
Модулі «Streamlink» є частиною «TVLINK».
{{% /hint %}}

{{< tabs >}}

{{% tab "LibreELEC/CoreELEC" %}}

## LibreELEC/CoreELEC

{{% hint info %}}
Маються на увазі модифіковані системи (ae-fork), в яких вже є всі необхідні залежності.
Робота програми в оригінальних ELEC-системах неможлива.
{{% /hint %}}

У налаштуваннях системи («LibreELEC/CoreELEC» -> «TV services» -> «TVLINK server») натисніть «Enable TVLINK».
Програма буде встановлена та запущена автоматично.

<p align="center">
  <img src="/tvlink/install/install-libre.png" />
</p>

{{% /tab %}}

{{% tab "Ubuntu/Debian/Armbian" %}}

## Ubuntu/Debian/Armbian

{{% hint info %}}
Пам’ятайте, що в системі має бути встановлена відповідна версія «Python». Версія «Python» вказана в назві файлу.
Наприклад: TVLINK-4.2.4-x86_64-**python_3.12**-Ubuntu.deb.
{{% /hint %}}

Для систем з архітектурою **x86-64** ви можете завантажити та встановити «TVLINK» за допомогою deb-пакета.
Завантажте потрібний файл і введіть команди в терміналі:

    apt install ./TVLINK-4.2.4-x86_64-python_3.12-Ubuntu.deb
    systemctl start tvlink
    systemctl enable tvlink

+ ### Armbian (aarch64)

Також ви можете встановити «TVLINK» з архіву.

{{% hint info %}}
На прикладі «Armbian Minimal/IOT Distro: Debian 12 (Bookworm)» для <a target='_blank' href="https://www.armbian.com/amlogic-s9xx-tv-box/">Amlogic S912</a>.
{{% /hint %}}

У «TVLINK» використовується утиліта «ping». Встановимо її, а також деякі утиліти, які нам знадобляться.

    apt install -y mc tar bzip2 wget iputils-ping

Встановимо залежності для «Streamlink» (python3-streamlink). Це можна зробити однією командою:

    apt install -y $(apt-cache depends python3-streamlink | grep Depends | sed "s/.*ends:\ //; s/<.*>//" | tr '\n' ' ')

{{% hint info %}}
Тут команда «apt-cache depends python3-streamlink» виводить інформацію про залежності модулів «Streamlink»,
а «grep, sed, tr» роблять з неї список, який передається команді «apt install».
{{% /hint %}}

Завантажимо та встановимо «TVLINK».

    mkdir -p /opt/tvlink
    cd /opt
    wget https://github.com/AlexELEC/TVLINK-Releases/releases/download/4.2.4/TVLINK-4.2.4-aarch64-python_3.11.tar.bz2 -O TVLINK.tar.bz2
    tar -jxf TVLINK.tar.bz2 --directory /opt/tvlink
    rm -f TVLINK.tar.bz2

Запустимо «TVLINK», щоб перевірити:

    root@armbian:/# /opt/tvlink/tvlink

    — Starting TVLINK (version: 4.2.4) on 127.0.0.1:2020 / 192.168.1.33:2020 —

Рекомендується зайти у веб-інтерфейс (наприклад: http://192.168.1.33:2020), додати канали та перевірити їхню роботу.
Помилки, пов’язані із залежностями, ви можете бачити лише в терміналі; до журналу роботи «TVLINK» вони не записуються.

Якщо все гаразд, завершіть роботу «TVLINK» (Ctrl+C) та додайте його до автозапуску системи.

    wget https://github.com/AlexELEC/TVLINK-Releases/raw/refs/heads/main/scripts/Ubuntu/tvlink.service -O /etc/systemd/system/tvlink.service
    
    systemctl enable tvlink
    systemctl start tvlink

{{% /tab %}}

{{% tab "OpenWRT (х86-64)" %}}

## OpenWRT (х86-64)

{{% hint info %}}
Простий спосіб встановлення системи OpenWRT для архітектури х86-64 описано тут.
{{% /hint %}}

{{% hint info %}}
Версія «OpenWRT», для якої скомпільована програма, вказана в описі релізу.
{{% /hint %}}

Оновімо репозиторії пакетів та встановимо залежності для модуля «Streamlink», що входить до складу «TVLINK».
Послідовно введімо команди в терміналі:

    opkg update
    opkg install python3 python3-certifi python3-chardet python3-cryptodome python3-pip python3-requests python3-six python3-lxml tar wget
    python -m pip install --upgrade pip
    pip install pycountry isodate pysocks

Завантажуємо та встановлюємо сам «TVLINK».

    wget https://github.com/AlexELEC/TVLINK-Releases/releases/download/4.2.4/TVLINK-4.2.4-x86_64-python_3.11-Openwrt.tar.bz2 -O TVLINK.tar.bz2
    mkdir -p /opt/tvlink
    tar -jxf TVLINK.tar.bz2 -C /opt/tvlink
    rm -f TVLINK.tar.bz2

Перевіряємо, чи працює програма.

    /opt/tvlink/tvlink

    — Starting TVLINK (version: 4.2.4) on 127.0.0.1:2020 / 192.168.1.1:2020 —

Рекомендується зайти у веб-інтерфейс (наприклад: http://192.168.1.1:2020), додати канали та перевірити їхню роботу.
Помилки, пов’язані із залежностями, ви можете бачити лише в терміналі; до журналу роботи «TVLINK» вони не записуються.

Якщо «TVLINK» працює без помилок, закрийте його (Ctrl+C). Завантажте та додайте сервіс до автозавантаження.

    cd /etc/init.d
    wget https://github.com/AlexELEC/TVLINK-Releases/raw/refs/heads/main/scripts/Openwrt/tvlink -O /etc/init.d/tvlink && chmod +x /etc/init.d/tvlink
    
    service tvlink enable
    service tvlink start

{{% /tab %}}

{{< /tabs >}}

## Оновлення програми

Як оновити програму, [читайте тут](/docs/tvlink/docs/status/#оновлення-програми).
