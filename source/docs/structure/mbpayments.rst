MBPayments
###########################################

Модуль приема платежей

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbpayments
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
    │   │   │       │   ├── config -> /var/bill/mbpayments/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbpayments
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbpayments
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
    │   │           │   ├── config -> /var/bill/mbpayments/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbpayments
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbpayments
    │   │                   └── index.php
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   └── index.php
    │   │   └── updates
    │   │       ├── mbpayments.current.checksum
    │   │       ├── mbpayments.downloaded.checksum
    │   │       └── mbpayments_update.sh
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   └── index.php
    │       └── updates
    │           ├── mbpayments.current.checksum
    │           ├── mbpayments.downloaded.checksum
    │           └── mbpayments_testing.sh
    ├── logs
    │   ├── mbpayments
    │   │   ├── mbpayments.debug
    │   │   ├── mbpayments.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbpayments/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/contrib
     - примонтированная директория системы /var/bill/contrib
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbpayments/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbpayments
   * - chroot/<version>/var/www/mbpayments
     - примонтированная директория системы /var/bill/mbpayments/<version>/public
   * - /var/bill/mbpayments/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbpayments
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbpayments
     - домашняя директория модуля
   * - /var/bill/mbpayments/production
     - production версия модуля
   * - /var/bill/mbpayments/testing
     - testing версия модуля
   * - <version>/backup
     - директория для бекапов (подключена из /var/bill/backup/mbpayments)
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом модуля
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbpayments_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbpayments.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbpayments.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbpayments
     - директория логов модуля
   * - /var/bill/logs/mbpayments/mbpayments.log
     - основной лог модуля
   * - /var/bill/logs/mbpayments/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbpayments/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbpayments.rst
.. include:: ../includes/updates/mbpayments.rst
.. include:: ../includes/cron/mbpayments.rst

.. include:: ../footer_links.rst