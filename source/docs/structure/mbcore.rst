mbcore
###########################################

Модуль используется для обработки Freeradius запросов (Access-Request/Accounting-Request) при авторизации абонентов.


Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbcore
    │   ├── production
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── kernel.php
    │   │   └── updates
    │   │       ├── kernel.current.checksum
    │   │       ├── kernel.downloaded.checksum
    │   │       └── mbcore_update.sh
    │   └── testing
    │       ├── config
    │       │   └── config.xml
    │       ├── kernel.php
    │       └── updates
    │           ├── kernel.current.checksum
    │           ├── kernel.downloaded.checksum
    │           └── mbcore_testing.sh
    ├── logs
    │   ├── mbcore
    │   │   ├── mbcore.debug
    │   │   ├── mbcore.log
    │   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table::
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbcore
     - домашняя директория модуля
   * - /var/bill/mbcore/production
     - production версия модуля
   * - /var/bill/mbcore/testing
     - testing версия модуля
   * - /var/bill/backup/mbsql
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/update
     - директория с файлами обновления
   * - <version>/update/mbcore_update.sh
     - загрузчик и установщик обновлений
   * - <version>/update/kernel.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/update/kernel.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbcore
     - директория логов модуля
   * - /var/bill/logs/mbcore/mbcore.log
     - основной лого модуля
   * - /var/bill/logs/mbcore/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbcore/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbcore.rst
.. include:: ../includes/updates/mbcore.rst
.. include:: ../includes/cron/mbcore.rst

.. include:: ../footer_links.rst