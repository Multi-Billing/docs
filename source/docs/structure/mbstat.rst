MBStat
###########################################

Модуль личного кабинета абонента

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbstat
    │   ├── chroot
    │   │   ├── production
    │   │   │   ├── bin -> usr/bin
    │   │   │   ├── dev
    │   │   │   ├── etc
    │   │   │   ├── home
    │   │   │   ├── lib -> usr/lib
    │   │   │   ├── lib64 -> usr/lib64
    │   │   │   ├── root
    │   │   │   ├── sbin -> usr/sbin
    │   │   │   ├── tmp
    │   │   │   ├── usr
    │   │   │   │   ├── bin
    │   │   │   │   ├── lib
    │   │   │   │   ├── lib64
    │   │   │   │   │   ├── gconv
    │   │   │   │   ├── sbin
    │   │   │   │   └── share
    │   │   │   │       ├── freeradius
    │   │   │   │       └── zoneinfo
    │   │   │   └── var
    │   │   │       ├── bill
    │   │   │       │   ├── config -> /var/bill/mbstat/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbstat
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbstat
    │   │   │               ├── data
    │   │   │               |   └── ...
    │   │   │               └── index.php
    │   │   └── testing
    │   │       ├── bin -> usr/bin
    │   │       ├── dev
    │   │       ├── etc
    │   │       ├── home
    │   │       ├── lib -> usr/lib
    │   │       ├── lib64 -> usr/lib64
    │   │       ├── root
    │   │       ├── sbin -> usr/sbin
    │   │       ├── tmp
    │   │       ├── usr
    │   │       │   ├── bin
    │   │       │   ├── lib
    │   │       │   ├── lib64
    │   │       │   │   ├── gconv
    │   │       │   ├── sbin
    │   │       │   └── share
    │   │       │       ├── freeradius
    │   │       │       └── zoneinfo
    │   │       └── var
    │   │           ├── bill
    │   │           │   ├── config -> /var/bill/mbstat/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbstat
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbstat
    │   │                   ├── data
    │   │                   |   └── ...
    │   │                   └── index.php
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   ├── data
    │   │   │   │   ├── locale
    │   │   │   │   └── template
    │   │   │   │       └── olson
    │   │   │   │           ├── css
    │   │   │   │           ├── customtpls
    │   │   │   │           ├── font
    │   │   │   │           ├── img
    │   │   │   │           ├── js
    │   │   │   │           └── webfonts
    │   │   │   └── index.php
    │   │   └── updates
    │   │       ├── mbstat.current.checksum
    │   │       ├── mbstat.downloaded.checksum
    │   │       └── mbstat_updater.sh
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   ├── data
    │       │   │   ├── locale
    │       │   │   └── template
    │       │   │       └── olson
    │       │   │           ├── css
    │       │   │           ├── customtpls
    │       │   │           ├── font
    │       │   │           ├── img
    │       │   │           ├── js
    │       │   │           └── webfonts
    │       │   └── index.php
    │       └── updates
    │           ├── mbstat.current.checksum
    │           ├── mbstat.downloaded.checksum
    │           └── mbstat_testing.sh
    ├── logs
    │   ├── mbstat
    │   │   ├── mbstat.debug
    │   │   ├── mbstat.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbstat/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbstat/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbstat
   * - chroot/<version>/var/www/mbstat
     - примонтированная директория системы /var/bill/mbstat/<version>/public
   * - /var/bill/mbstat/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbstat
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbstat
     - домашняя директория модуля
   * - /var/bill/mbstat/production
     - production версия модуля
   * - /var/bill/mbstat/testing
     - testing версия модуля
   * - /var/bill/backup/mbstat
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbstat_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbstat.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbstat.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbstat
     - директория логов модуля
   * - /var/bill/logs/mbstat/mbstat.log
     - основной лог модуля
   * - /var/bill/logs/mbstat/mbstat.debug
     - debug лог модуля
   * - /var/bill/logs/mbstat/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbstat.rst
.. include:: ../includes/updates/mbstat.rst
.. include:: ../includes/cron/mbstat.rst

.. include:: ../footer_links.rst