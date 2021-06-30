mbpaygw
###########################################

Модуль приема платежей

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbpaygw
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
    │   │   │       │   ├── config -> /var/bill/mbpaygw/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbpaygw
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbpaygw
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
    │   │           │   ├── config -> /var/bill/mbpaygw/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbpaygw
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbpaygw
    │   │                   └── index.php
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   └── index.php
    │   │   └── updates
    │   │       ├── mbpaygw.current.checksum
    │   │       ├── mbpaygw.downloaded.checksum
    │   │       └── mbpaygw_update.sh
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   └── index.php
    │       └── updates
    │           ├── mbpaygw.current.checksum
    │           ├── mbpaygw.downloaded.checksum
    │           └── mbpaygw_testing.sh
    ├── logs
    │   ├── mbpaygw
    │   │   ├── mbpaygw.debug
    │   │   ├── mbpaygw.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbpaygw/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/contrib
     - примонтированная директория системы /var/bill/contrib
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbpaygw/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbpaygw
   * - chroot/<version>/var/www/mbpaygw
     - примонтированная директория системы /var/bill/mbpaygw/<version>/public
   * - /var/bill/mbpaygw/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbpaygw
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbpaygw
     - домашняя директория модуля
   * - /var/bill/mbpaygw/production
     - production версия модуля
   * - /var/bill/mbpaygw/testing
     - testing версия модуля
   * - <version>/backup
     - директория для бекапов (подключена из /var/bill/backup/mbpaygw)
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbpaygw_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbpaygw.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbpaygw.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbpaygw
     - директория логов модуля
   * - /var/bill/logs/mbpaygw/mbpaygw.log
     - основной лог модуля
   * - /var/bill/logs/mbpaygw/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbpaygw/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbpaygw.rst
.. include:: ../includes/updates/mbpaygw.rst
.. include:: ../includes/cron/mbpaygw.rst

.. include:: ../footer_links.rst