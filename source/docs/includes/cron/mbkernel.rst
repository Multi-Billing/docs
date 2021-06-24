Задания cron
*************************************************

- Файл с заданиями модуля расположен по пути ``/etc/cron.d/mbkernel`` и содержит задания

  * синхронизация времени на сервере
  * запуск обновления production версии модуля


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

    # sync time
    0 * * * *  root /usr/bin/chronyc -a 'burst 4/4' > /dev/null 2>&1

    # update
    05 6 * * * root /var/bill/mbkernel/production/updates/mbkernel_update.sh
