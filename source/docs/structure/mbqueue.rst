MBQueue
###########################################

Модуль обработки отложенных заданий и команд

Файловая структура модуля
*******************************************

.. code-block:: bash

    /var/bill
    ├── mbqueue
    │   ├── production
    │   │   ├── backup -> /var/bill/backup/mbqueue
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
    │   │   └── update
    │   │       ├── mbqueue.current.checksum
    │   │       ├── mbqueue.downloaded.checksum
    │   │       └── mbqueue_update.sh
    │   └── testing
    │       ├── backup -> /var/bill/backup/mbqueue
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
    │       └── update
    │           ├── mbqueue.current.checksum
    │           ├── mbqueue.downloaded.checksum
    │           └── mbqueue_testing.sh
    ├── logs
    │   ├── mbqueue
    │   │   ├── debug.log
    │   │   ├── mbqueue.log
    │   │   └── update.log
    ├── contrib
    │   ├── custom
    │   ├── documents
    │   │   ├── check_horz.html
    │   │   ├── check.html
    │   │   ├── check_vert.html
    │   │   ├── dogovor2.htm
    │   │   ├── dogovor3.htm
    │   │   ├── dogovor4.htm
    │   │   ├── dogovor5.htm
    │   │   ├── dogovor6.htm
    │   │   ├── dogovor.htm
    │   │   ├── dogovor_legal2.htm
    │   │   ├── dogovor_legal3.htm
    │   │   ├── dogovor_legal4.htm
    │   │   ├── dogovor_legal5.htm
    │   │   ├── dogovor_legal6.htm
    │   │   ├── dogovor_legal.htm
    │   │   ├── final_report.htm
    │   │   ├── pamyatka.htm
    │   │   ├── tickets_body.htm
    │   │   ├── tickets_bottom.htm
    │   │   └── tickets_header.htm
    │   ├── files
    │   ├── mrtg
    │   └── scripts
    │       ├── cpu_info.sh
    │       ├── current_ram.sh
    │       ├── disk_partitions.sh
    │       ├── logged_in_users.sh
    │       ├── mb_event_iptv_add.sh
    │       ├── mb_event_iptv_del.sh
    │       ├── mb_event_port_change.sh
    │       ├── mb_event_realip_change.sh
    │       ├── mb_event_switch_change.sh
    │       ├── mb_event_ticket_close.sh
    │       ├── mb_event_ticket_message.sh
    │       ├── mb_event_ticket_open.sh
    │       ├── onoff_user_event.sh
    │       ├── payment_event.sh
    │       ├── pcq.sh
    │       ├── pingerarp.sh
    │       ├── pinger.sh
    │       ├── port_restart_event.sh
    │       ├── ram_info.sh
    │       └── tarif_change_event.sh

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
   * - <version>/backup
     - директория для бекапов (подключена из /var/bill/backup/mbqueue)
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
   * - <version>/scripts/update_bras.sh
     - bash скрипт с набором команд обновления данных для dashboard
   * - <version>/scripts/update_cpu.sh
     - bash скрипт с набором команд обновления данных для dashboard
   * - <version>/scripts/update_dev.sh
     - bash скрипт с набором команд обновления данных для dashboard
   * - <version>/scripts/update_ram.sh
     - bash скрипт с набором команд обновления данных для dashboard
   * - <version>/update
     - директория с файлами обновления
   * - <version>/update/mbqueue_update.sh
     - загрузчик и установщик обновлений
   * - <version>/update/mbqueue.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/update/mbqueue.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений
   * - /var/bill/logs/mbqueue
     - директория логов модуля
   * - /var/bill/logs/mbqueue/mbqueue.log
     - основной лог модуля
   * - /var/bill/logs/mbqueue/debug.log
     - debug лог модуля
   * - /var/bill/logs/mbqueue/update.log
     - лог обновлений модуля

.. include:: ../includes/config/mbqueue.rst
.. include:: ../includes/updates/mbqueue.rst
.. include:: ../includes/cron/mbqueue.rst

.. include:: ../footer_links.rst