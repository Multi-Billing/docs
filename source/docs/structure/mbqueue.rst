MBQueue
###########################################

Модуль обработки отложенных заданий и команд

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbqueue
    │   ├── production
    │   │   ├── config
    │   │   │   └── config.xml
    │   │   ├── index.php
    │   │   ├── scripts
    │   │   │   ├── 5min.sh
    │   │   │   ├── block.sh
    │   │   │   ├── day.sh
    │   │   │   ├── lastday.sh
    │   │   │   ├── mrtg.sh
    │   │   │   ├── mth.sh
    │   │   │   ├── update_bras.sh
    │   │   │   ├── update_cpu.sh
    │   │   │   ├── update_dev.sh
    │   │   │   └── update_ram.sh
    │   │   └── updates
    │   │       ├── mbqueue.current.checksum
    │   │       ├── mbqueue.downloaded.checksum
    │   │       └── mbqueue_update.sh
    │   └── testing
    │       ├── config
    │       │   └── config.xml
    │       ├── index.php
    │       ├── scripts
    │       │   ├── 5min.sh
    │       │   ├── block.sh
    │       │   ├── day.sh
    │       │   ├── lastday.sh
    │       │   ├── mrtg.sh
    │       │   ├── mth.sh
    │       │   ├── update_bras.sh
    │       │   ├── update_cpu.sh
    │       │   ├── update_dev.sh
    │       │   └── update_ram.sh
    │       └── updates
    │           ├── mbqueue.current.checksum
    │           ├── mbqueue.downloaded.checksum
    │           └── mbqueue_testing.sh
    ├── logs
    │   ├── mbqueue
    │   │   ├── mbqueue.debug
    │   │   ├── mbqueue.log
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
   * - /var/bill/mbqueue
     - домашняя директория модуля
   * - /var/bill/mbqueue/production
     - production версия модуля
   * - /var/bill/mbqueue/testing
     - testing версия модуля
   * - /var/bill/backup/mbqueue
     - директория для бекапов
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/index.php
     - файл с кодом модуля
   * - <version>/scripts
     - директория с скриптами модуля
   * - <version>/scripts/5min.sh
     - bash скрипт с набором команд которые необходимо переодически запускать
   * - <version>/scripts/block.sh
     - bash скрипт с набором команд для блокировки абонентов по балансу
   * - <version>/scripts/day.sh
     - bash скрипт с набором команд для ежедневных снятий абонплаты
   * - <version>/scripts/mth.sh
     - bash скрипт с набором команд для ежемесчных снятий абонплаты
   * - <version>/scripts/lastday.sh
     - bash скрипт с набором команд которые необходимо запускать в конце месяца
   * - <version>/scripts/mrtg.sh
     - bash скрипт с командами генерации mrtg графиков
   * - <version>/updates
     - директория с файлами обновления
   * - <version>/updates/mbqueue_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbqueue.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbqueue.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbqueue
     - директория логов модуля
   * - /var/bill/logs/mbqueue/mbqueue.log
     - основной лог модуля
   * - /var/bill/logs/mbqueue/mbqueue.debug
     - debug лог модуля
   * - /var/bill/logs/mbqueue/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbqueue.rst
.. include:: ../includes/updates/mbqueue.rst
.. include:: ../includes/cron/mbqueue.rst

.. include:: ../footer_links.rst