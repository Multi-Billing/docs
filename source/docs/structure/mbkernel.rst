MBKernel
###########################################

Модуль используется для обработки Freeradius запросов (Access-Request/Accounting-Request) при авторизации абонентов.


Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbkernel
    │   ├── production
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── kernel.php
    │   │   └── updates
    │   │       ├── kernel.current.checksum
    │   │       ├── kernel.downloaded.checksum
    │   │       └── mbkernel_update.sh
    │   └── testing
    │       ├── config
    │       │   └── config.xml
    │       ├── kernel.php
    │       └── updates
    │           ├── kernel.current.checksum
    │           ├── kernel.downloaded.checksum
    │           └── mbkernel_testing.sh
    ├── logs
    │   ├── mbkernel
    │   │   ├── mbkernel.debug
    │   │   ├── mbkernel.log
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
   * - /var/bill/mbkernel
     - домашняя директория модуля
   * - /var/bill/mbkernel/production
     - production версия модуля
   * - /var/bill/mbkernel/testing
     - testing версия модуля
   * - /var/bill/backup/mbdbupdate
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/update
     - директория с файлами обновления
   * - <version>/update/mbkernel_update.sh
     - загрузчик и установщик обновлений
   * - <version>/update/kernel.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/update/kernel.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbkernel
     - директория логов модуля
   * - /var/bill/logs/mbkernel/mbkernel.log
     - основной лого модуля
   * - /var/bill/logs/mbkernel/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbkernel/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbkernel.rst
.. include:: ../includes/updates/mbkernel.rst
.. include:: ../includes/cron/mbkernel.rst

.. include:: ../footer_links.rst