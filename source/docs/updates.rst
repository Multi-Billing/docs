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
   * - mbcore
     - `mbcore_update.sh <http://free.update.multi-billing.pro/mbcore_update.sh>`_
     - `mbcore_testing.sh <http://free.current.multi-billing.pro/mbcore_testing.sh>`_
   * - mbsql
     - `mbsql_update.sh <http://free.update.multi-billing.pro/mbsql_update.sh>`_
     - `mbsql_testing.sh <http://free.current.multi-billing.pro/mbsql_testing.sh>`_
   * - mbcron
     - `mbcron_update.sh <http://free.update.multi-billing.pro/mbcron_update.sh>`_
     - `mbcron_testing.sh <http://free.current.multi-billing.pro/mbcron_testing.sh>`_
   * - mbpaygw
     - `mbpaygw_update.sh <http://free.update.multi-billing.pro/mbpaygw_update.sh>`_
     - `mbpaygw_testing.sh <http://free.current.multi-billing.pro/mbpaygw_testing.sh>`_
   * - mbcabapi
     - `mbcabapi_update.sh <http://free.update.multi-billing.pro/mbcabapi_update.sh>`_
     - `mbcabapi_testing.sh <http://free.current.multi-billing.pro/mbcabapi_testing.sh>`_
   * - mbcabinet
     - `mbcabinet_update.sh <http://free.update.multi-billing.pro/mbcabinet_update.sh>`_
     - `mbcabinet_testing.sh <http://free.current.multi-billing.pro/mbcabinet_testing.sh>`_

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

  tar -xzvf /var/bill/backup/mbcabinet/mbcabinet_production.2020-09-28_11-53.tar.gz /var/bill/mbcabinet/production/public


Тестовые обновления
*******************************************

Тестовые обновления - это специальная "сборка" которая включает в себя актуальную версию обновления + наработки которые на данный момент готовы для следующего обновления (новый функционал, багфиксы, новые баги и т.п.).

Для установки тестового обновления необходимо перейти в тестовую директорию модуля и запустить скрипт тестовго обновления:

.. code-block:: sh

  bash /var/bill/mbcabinet/testing/update/mbcabinet_testing.sh

