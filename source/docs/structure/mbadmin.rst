mbadmin
###########################################

Модуль для работы с биллингом, состоит из backend (логика) и frontend (интерфейс) частей

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbadmin
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
    │   │   │   └── var
    │   │   │       ├── bill
    │   │   │       │   ├── config -> /var/bill/mbadmin/production/config
    │   │   │       │   └── logs -> /var/bill/logs/mbadmin
    │   │   │       ├── lib
    │   │   │       │   └── php
    │   │   │       │       └── session
    │   │   │       ├── log
    │   │   │       │   └── php-fpm
    │   │   │       └── www
    │   │   │           └── mbadmin
    │   │   │               ├── cache.appcache
    │   │   │               ├── classic.json
    │   │   │               ├── classic.jsonp
    │   │   │               ├── index.html
    │   │   │               ├── index.php
    │   │   │               ├── MBPlatform
    │   │   │               │	└── ..
    │   │   │               ├── modern.json
    │   │   │               └── modern.jsonp
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
    │   │       └── var
    │   │           ├── bill
    │   │           │   ├── config -> /var/bill/mbadmin/testing/config
    │   │           │   └── logs -> /var/bill/logs/mbadmin
    │   │           ├── lib
    │   │           │   └── php
    │   │           │       └── session
    │   │           ├── log
    │   │           │   └── php-fpm
    │   │           └── www
    │   │               └── mbadmin
    │   │                   ├── cache.appcache
    │   │                   ├── classic.json
    │   │                   ├── classic.jsonp
    │   │                   ├── index.html
    │   │                   ├── index.php
    │   │                   ├── MBPlatform
    │   │                   │	└── ..
    │   │                   ├── modern.json
    │   │                   └── modern.jsonp
    │   ├── production
    │   │   ├── add_to_chroot.sh
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── public
    │   │   │   ├── cache.appcache
    │   │   │   ├── classic.json
    │   │   │   ├── classic.jsonp
    │   │   │   ├── index.html
    │   │   │   ├── index.php
    │   │   │   ├── MBPlatform
    │   │   │   │	└── ..
    │   │   │   ├── modern.json
    │   │   │   └── modern.jsonp
    │   │   └── updates
    │   │       ├── mbadmin_backend_update.sh
    │   │       ├── mbadmin.current.checksum
    │   │       ├── mbadmin.downloaded.checksum
    │   │       ├── mbadmin_frontend_update.sh
    │   │       ├── mbfront.current.checksum
    │   │       └── mbfront.downloaded.checksum
    │   └── testing
    │       ├── add_to_chroot.sh
    │       ├── config
    │       │   └── config.xml
    │       ├── public
    │       │   ├── cache.appcache
    │       │   ├── classic.json
    │       │   ├── classic.jsonp
    │       │   ├── index.html
    │       │   ├── index.php
    │       │   ├── MBPlatform
    │       │   │	└── ..
    │       │   ├── modern.json
    │       │   └── modern.jsonp
    │       └── updates
    │           ├── mbadmin_backend_testing.sh
    │           ├── mbadmin.current.checksum
    │           ├── mbadmin.downloaded.checksum
    │           ├── mbadmin_frontend_testing.sh
    │           ├── mbfront.current.checksum
    │           └── mbfront.downloaded.checksum
    ├── logs
    │   ├── mbadmin
    │   │   ├── mbadmin.debug
    │   │   ├── mbadmin.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: chroot среда модуля
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbadmin/chroot/<version>
     - корневая директория chroot среды
   * - chroot/<version>/var/bill/config
     - примонтированная директория системы /var/bill/mbadmin/<version>/config
   * - chroot/<version>/var/bill/logs
     - примонтированная директория системы /var/bill/logs/mbadmin
   * - chroot/<version>/var/www/mbadmin
     - примонтированная директория системы /var/bill/mbadmin/<version>/public
   * - /var/bill/mbadmin/<version>/add_to_chroot.sh
     - скрипт для добавления программ в изолированную chroot среду

.. list-table:: модуль mbadmin
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill/mbadmin
     - домашняя директория модуля
   * - /var/bill/mbadmin/production
     - production версия модуля
   * - /var/bill/mbadmin/testing
     - testing версия модуля
   * - /var/bill/backup/mbadmin
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/public
     - WWW директория модуля (подключается в chroot среду)
   * - <version>/public/index.php
     - файл с кодом backend части модуля
   * - <version>/public/index.html
     - файл с кодом frontend части модуля
   * - <version>/public/MBPlatform
     - директория frontend модуля
   * - <version>/public/cache.appcache
     - манифест кеша frontend
   * - <version>/public/classic.json
     - файл с внутренней конфигурацией frontend
   * - <version>/public/classic.jsonp
     - файл с внутренней конфигурацией frontend
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbadmin_backend_update.sh
     - загрузчик и установщик обновлений backend части модуля
   * - <version>/updates/mbadmin_frontend_update.sh
     - загрузчик и установщик обновлений frontend части модуля
   * - <version>/updates/mbadmin.current.checksum
     - файл с md5 суммой текущей версии обновлений backend части модуля
   * - <version>/updates/mbadmin.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений backend части модуля
   * - <version>/updates/mbfront.current.checksum
     - файл с md5 суммой текущей версии обновлений frontend части модуля
   * - <version>/updates/mbfront.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений frontend части модуля
   * - /var/bill/logs/mbadmin
     - директория логов модуля
   * - /var/bill/logs/mbadmin/mbadmin.log
     - основной лог модуля
   * - /var/bill/logs/mbadmin/mbadmin.debug
     - debug лог модуля
   * - /var/bill/logs/mbadmin/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbadmin.rst
.. include:: ../includes/updates/mbadmin.rst
.. include:: ../includes/cron/mbadmin.rst

.. include:: ../footer_links.rst