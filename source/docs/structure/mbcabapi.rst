MBCabinetAPI
###########################################

Модуль API Личного кабинета

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbcabapi
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
    │   │   │   │   ├── sbin
    │   │   │   │   └── share
    │   │   │   │       ├── freeradius
    │   │   │   │       └── zoneinfo
    │   │   │   └── var
    │   │   │       ├── bill
    │   │   │       │   ├── config -> /var/bill/mbcabapi/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbcabapi
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbcabapi
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
    │   │       │   ├── sbin
    │   │       │   └── share
    │   │       │       ├── freeradius
    │   │       │       └── zoneinfo
    │   │       └── var
    │   │           ├── bill
    │   │           │   ├── config -> /var/bill/mbcabapi/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbcabapi
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbcabapi
    │   │                   └── index.php
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   └── index.php
    │   │   └── updates
    │   │       ├── mbcabapi.current.checksum
    │   │       ├── mbcabapi.downloaded.checksum
    │   │       └── mbcabapi_update.sh
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   └── index.php
    │       └── updates
    │           ├── mbcabapi.current.checksum
    │           ├── mbcabapi.downloaded.checksum
    │           └── mbcabapi_testing.sh
    ├── logs
    │   ├── mbcabapi
    │   │   ├── mbcabapi.debug
    │   │   ├── mbcabapi.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbcabapi/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbcabapi/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbcabapi
   * - chroot/<version>/var/www/mbcabapi
     - примонтированная директория системы /var/bill/mbcabapi/<version>/public
   * - /var/bill/mbcabapi/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbcabinet
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbcabapi
     - домашняя директория модуля
   * - /var/bill/mbcabapi/production
     - production версия модуля
   * - /var/bill/mbcabapi/testing
     - testing версия модуля
   * - /var/bill/backup/mbcabapi
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbcabapi_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbcabapi.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbcabapi.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbcabapi
     - директория логов модуля
   * - /var/bill/logs/mbcabapi/mbcabinet.log
     - основной лог модуля
   * - /var/bill/logs/mbcabapi/mbcabinet.debug
     - debug лог модуля
   * - /var/bill/logs/mbcabapi/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbcabapi.rst
.. include:: ../includes/updates/mbcabapi.rst
.. include:: ../includes/cron/mbcabapi.rst

.. include:: ../footer_links.rst