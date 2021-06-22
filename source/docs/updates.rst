Обновления
###########################################

| Обновления выходят в среднем раз в 3-4 недели (зависит от загруженности).

Адрес сервера обновлений
*******************************************

.. list-table:: 
   :widths: 100 100
   :header-rows: 1

   * - Production
     - Testing
   * - free.update.multi-billing.pro
     - free.current.multi-billing.pro
   * - pay.update.multi-billing.pro
     - pay.current.multi-billing.pro

Скрипты обновлений
*******************************************

.. list-table:: 
   :widths: 100 100 100
   :header-rows: 1

   * - Модуль
     - Production версия
     - Testing версия
   * - mbadmin - backend
     - `mbadmin_backend_update.sh <http://free.update.multi-billing.pro/mbadmin_backend_update.sh>`_
     - `mbadmin_backend_testing.sh <http://free.current.multi-billing.pro/mbadmin_backend_testing.sh>`_
   * - mbadmin - frontend
     - `mbadmin_frontend_update.sh <http://free.update.multi-billing.pro/mbadmin_frontend_update.sh>`_
     - `mbadmin_frontend_testing.sh <http://free.current.multi-billing.pro/mbadmin_frontend_testing.sh>`_
   * - mbkernel
     - `mbkernel_update.sh <http://free.update.multi-billing.pro/mbkernel_update.sh>`_
     - `mbkernel_testing.sh <http://free.current.multi-billing.pro/mbkernel_testing.sh>`_
   * - mbdbupdate
     - `mbdbupdate_update.sh <http://free.update.multi-billing.pro/mbdbupdate_update.sh>`_
     - `mbdbupdate_testing.sh <http://free.current.multi-billing.pro/mbdbupdate_testing.sh>`_
   * - mbqueue
     - `mbqueue_update.sh <http://free.update.multi-billing.pro/mbqueue_update.sh>`_
     - `mbqueue_testing.sh <http://free.current.multi-billing.pro/mbqueue_testing.sh>`_
   * - mbpayments
     - `mbpayments_update.sh <http://free.update.multi-billing.pro/mbpayments_update.sh>`_
     - `mbpayments_testing.sh <http://free.current.multi-billing.pro/mbpayments_testing.sh>`_
   * - mbcabapi
     - `mbcabapi_update.sh <http://free.update.multi-billing.pro/mbcabapi_update.sh>`_
     - `mbcabapi_testing.sh <http://free.current.multi-billing.pro/mbcabapi_testing.sh>`_
   * - mbstat
     - `mbstat_update.sh <http://free.update.multi-billing.pro/mbstat_update.sh>`_
     - `mbstat_testing.sh <http://free.current.multi-billing.pro/mbstat_testing.sh>`_

Автоматическое обновлене
*******************************************

По умолчанию обновление включено для каждого модуля и процесс обновления запускается каждый день в 06:05
Обновление происходит из ``cron``, каждый модуль имеет свой файл с задачами в ``/etc/cron.d/``


Ручное обновление
*******************************************

Запустить скрипт обновления нужного модуля с ключем ``-f`` (force) 

.. code-block:: sh

  bash /var/bill/<module_name>/production/update/<updater_name>.sh -f


Откат обновления
*******************************************

| Перед установкой новой версии, скрипт обновления создает бекап текущей версии.
| Бекапы создаются в ``/var/bill/backup/<module_name>`` в формате ``<moduel_name>_<version>.дата_время.tar.gz``
| Принцип отката обновления один для всех архивов, найти нужный бекап и распаковать его в рабочую директорию модуля:

.. code-block:: sh

  tar -xzvf /var/bill/backup/mbstat/mbstat_production.2020-09-28_11-53.tar.gz /var/bill/mbstat/production/public


Тестовые обновления
*******************************************

Тестовые обновления - это специальная "сборка" которая включает в себя актуальную версию обновления + наработки которые на данный момент готовы для следующего обновления (новый функционал, багфиксы, новые баги и т.п.).

Для установки тестового обновления необходимо перейти в тестовую директорию модуля и запустить скрипт тестовго обновления:

.. code-block:: sh

  bash /var/bill/mbstat/testing/update/mbstat_testing.sh

