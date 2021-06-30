mbcron
###########################################

Модуль обработки отложенных заданий и команд

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbcron
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
    │   │       ├── mbcron.current.checksum
    │   │       ├── mbcron.downloaded.checksum
    │   │       └── mbcron_update.sh
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
    │           ├── mbcron.current.checksum
    │           ├── mbcron.downloaded.checksum
    │           └── mbcron_testing.sh
    ├── logs
    │   ├── mbcron
    │   │   ├── mbcron.debug
    │   │   ├── mbcron.log
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
   * - /var/bill/mbcron
     - домашняя директория модуля
   * - /var/bill/mbcron/production
     - production версия модуля
   * - /var/bill/mbcron/testing
     - testing версия модуля
   * - /var/bill/backup/mbcron
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
   * - <version>/updates/mbcron_update.sh
     - загрузчик и установщик обновлений
   * - <version>/updates/mbcron.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/updates/mbcron.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbcron
     - директория логов модуля
   * - /var/bill/logs/mbcron/mbcron.log
     - основной лог модуля
   * - /var/bill/logs/mbcron/mbcron.debug
     - debug лог модуля
   * - /var/bill/logs/mbcron/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbcron.rst
.. include:: ../includes/updates/mbcron.rst
.. include:: ../includes/cron/mbcron.rst

.. include:: ../footer_links.rst