mbhookpaygw
###########################################

Модуль приема платежей

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbhookpaygw
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
    │   │   │       │   ├── config -> /var/bill/mbhookpaygw/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbhookpaygw
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbhookpaygw
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
    │   │           │   ├── config -> /var/bill/mbhookpaygw/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbhookpaygw
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbhookpaygw
    │   │                   └── index.php
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   └── index.php
    │   │   └── updates
    │   │       ├── mbhookpaygw.current.checksum
    │   │       ├── mbhookpaygw.downloaded.checksum
    │   │       └── mbhookpaygw_update.sh
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   └── index.php
    │       └── updates
    │           ├── mbhookpaygw.current.checksum
    │           ├── mbhookpaygw.downloaded.checksum
    │           └── mbhookpaygw_testing.sh
    ├── logs
    │   ├── mbhookpaygw
    │   │   ├── mbhookpaygw.debug
    │   │   ├── mbhookpaygw.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbhookpaygw/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/contrib
     - примонтированная директория системы /var/bill/contrib
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbhookpaygw/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbhookpaygw
   * - chroot/<version>/var/www/mbhookpaygw
     - примонтированная директория системы /var/bill/mbhookpaygw/<version>/public
   * - /var/bill/mbhookpaygw/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbhookpaygw
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbhookpaygw
     - домашняя директория модуля
   * - /var/bill/mbhookpaygw/production
     - production версия модуля
   * - /var/bill/mbhookpaygw/testing
     - testing версия модуля
   * - <version>/backup
     - директория для бекапов (подключена из /var/bill/backup/mbhookpaygw)
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbhookpaygw_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbhookpaygw.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbhookpaygw.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbhookpaygw
     - директория логов модуля
   * - /var/bill/logs/mbhookpaygw/mbhookpaygw.log
     - основной лог модуля
   * - /var/bill/logs/mbhookpaygw/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbhookpaygw/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbpaygw.rst
.. include:: ../includes/updates/mbpaygw.rst
.. include:: ../includes/cron/mbpaygw.rst

.. include:: ../footer_links.rst