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
    │   │   │   │   ├── null
    │   │   │   │   ├── random
    │   │   │   │   ├── urandom
    │   │   │   │   └── zero
    │   │   │   ├── etc
    │   │   │   │   ├── hosts
    │   │   │   │   ├── localtime
    │   │   │   │   └── resolv.conf
    │   │   │   ├── home
    │   │   │   ├── lib -> usr/lib
    │   │   │   ├── lib64 -> usr/lib64
    │   │   │   ├── root
    │   │   │   ├── sbin -> usr/sbin
    │   │   │   ├── tmp
    │   │   │   ├── usr
    │   │   │   │   ├── bin
    │   │   │   │   │   ├── awk
    │   │   │   │   │   ├── bash
    │   │   │   │   │   ├── cat
    │   │   │   │   │   ├── command
    │   │   │   │   │   ├── date
    │   │   │   │   │   ├── echo
    │   │   │   │   │   ├── free
    │   │   │   │   │   ├── grep
    │   │   │   │   │   ├── ls
    │   │   │   │   │   ├── php
    │   │   │   │   │   ├── radclient
    │   │   │   │   │   ├── rm
    │   │   │   │   │   ├── sed
    │   │   │   │   │   └── sh
    │   │   │   │   ├── lib
    │   │   │   │   ├── lib64
    │   │   │   │   ├── sbin
    │   │   │   │   └── share
    │   │   │   │       ├── freeradius
    │   │   │   │       └── zoneinfo
    │   │   │   └── var
    │   │   │       ├── bill
    │   │   │       │   ├── config -> /var/bill/mbpayments/production/config
    │   │   │       │   ├── contrib -> /var/bill/contrib
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
    │   │       │   ├── null
    │   │       │   ├── random
    │   │       │   ├── urandom
    │   │       │   └── zero
    │   │       ├── etc
    │   │       │   ├── hosts
    │   │       │   ├── localtime
    │   │       │   └── resolv.conf
    │   │       ├── home
    │   │       ├── lib -> usr/lib
    │   │       ├── lib64 -> usr/lib64
    │   │       ├── root
    │   │       ├── sbin -> usr/sbin
    │   │       ├── tmp
    │   │       ├── usr
    │   │       │   ├── bin
    │   │       │   │   ├── awk
    │   │       │   │   ├── bash
    │   │       │   │   ├── cat
    │   │       │   │   ├── command
    │   │       │   │   ├── date
    │   │       │   │   ├── echo
    │   │       │   │   ├── free
    │   │       │   │   ├── grep
    │   │       │   │   ├── ls
    │   │       │   │   ├── php
    │   │       │   │   ├── radclient
    │   │       │   │   ├── rm
    │   │       │   │   ├── sed
    │   │       │   │   └── sh
    │   │       │   ├── lib
    │   │       │   ├── lib64
    │   │       │   ├── sbin
    │   │       │   └── share
    │   │       │       ├── freeradius
    │   │       │       └── zoneinfo
    │   │       └── var
    │   │           ├── bill
    │   │           │   ├── config -> /var/bill/mbpayments/testing/config
    │   │           │   ├── contrib -> /var/bill/contrib
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
    │   │   ├── backup -> /var/bill/backup/mbpayments
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
    │       ├── backup -> /var/bill/backup/mbpayments
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