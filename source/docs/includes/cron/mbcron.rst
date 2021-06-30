Задания cron
*************************************************

- Файл с заданиями модуля расположен по пути ``/etc/cron.d/mbcron_production`` и содержит задания

  * запуск обновления production версии модуля
  * запуск переодичных заданий из скрипта **5min.sh**
  * запуск скрипта для блокировки абонентов по балансу (**block.sh**)
  * запуск скрипта для снятия абонплаты (**day.sh**, **mth.sh**)
  * запуск скрипта для заданий выполняющихся в конце месяца (**lastday.sh**)
  * запуск скрипта для генерации графиков mrtg

.. code-block:: bash

    # For details see man 4 crontabs

    # Example of job definition:
    # .---------------- minute (0 - 59)
    # |  .------------- hour (0 - 23)
    # |  |  .---------- day of month (1 - 31)
    # |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
    # |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
    # |  |  |  |  |
    # *  *  *  *  * user-name  command to be executed

    # update
    05 6 * * * root /var/bill/mbcron/production/updates/mbcron_update.sh

    # billing tasks
    0-59/5 * * * * root /var/bill/mbcron/production/scripts/5min.sh

    # mrtg graph
    0-59/5 * * * * root /var/bill/mbcron/production/scripts/mrtg.sh

    # daily write-offs
    57 23 * * * root /var/bill/mbcron/production/scripts/block.sh
    58 23 * * * root /var/bill/mbcron/production/scripts/day.sh

    # monthly write-offs
    59 23 28-31 * * root [ "$(date +%d -d tomorrow)" = "01" ] && /var/bill/mbcron/production/scripts/lastday.sh
    01 0 1 * * root /var/bill/mbcron/production/scripts/mth.sh
