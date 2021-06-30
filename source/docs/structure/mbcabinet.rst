mbcabinet
###########################################

Модуль личного кабинета абонента

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbcabinet
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
    │   │   │       │   ├── config -> /var/bill/mbcabinet/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbcabinet
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbcabinet
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
    │   │           │   ├── config -> /var/bill/mbcabinet/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbcabinet
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbcabinet
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
    │   │       ├── mbcabinet.current.checksum
    │   │       ├── mbcabinet.downloaded.checksum
    │   │       └── mbcabinet_updater.sh
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
    │           ├── mbcabinet.current.checksum
    │           ├── mbcabinet.downloaded.checksum
    │           └── mbcabinet_testing.sh
    ├── logs
    │   ├── mbcabinet
    │   │   ├── mbcabinet.debug
    │   │   ├── mbcabinet.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbcabinet/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbcabinet/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbcabinet
   * - chroot/<version>/var/www/mbcabinet
     - примонтированная директория системы /var/bill/mbcabinet/<version>/public
   * - /var/bill/mbcabinet/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbcabinet
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbcabinet
     - домашняя директория модуля
   * - /var/bill/mbcabinet/production
     - production версия модуля
   * - /var/bill/mbcabinet/testing
     - testing версия модуля
   * - /var/bill/backup/mbcabinet
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbcabinet_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbcabinet.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbcabinet.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbcabinet
     - директория логов модуля
   * - /var/bill/logs/mbcabinet/mbcabinet.log
     - основной лог модуля
   * - /var/bill/logs/mbcabinet/mbcabinet.debug
     - debug лог модуля
   * - /var/bill/logs/mbcabinet/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbcabinet.rst
.. include:: ../includes/updates/mbcabinet.rst
.. include:: ../includes/cron/mbcabinet.rst

.. include:: ../footer_links.rst