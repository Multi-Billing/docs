Файл конфигурации
*************************************************

Файл расположен по пути ``/var/bill/mbkernel/<version>/config/config.xml``

.. code-block:: xml

    <config>
      <parameters>
        <mysql>
          <host>DATABASE_IP</host>
          <username>DATABASE_USER</username>
          <password>DATABASE_PASSWORD</password>
          <dbname>DATABASE_NAME</dbname>
        </mysql>
        <kernel>
          <ip>127.0.0.1</ip>
          <port>22007</port>
          <pid>/var/run/mbkernel/kernel_production.pid</pid>
          <log>/var/bill/logs/mbkernel/mbkernel.log</log>
          <debug>false</debug>
          <debug_log>/var/bill/logs/mbkernel/debug.log</debug_log>
          <request_timing>3.000001</request_timing>
        </kernel>
      <timezone>Europe/Kiev</timezone>
      </parameters>
    </config>

.. list-table::
   :widths: 100 100
   :header-rows: 1

   * - параметр
     - описание
   * - mysql секция
     -
   * - host
     - IP адрес базы данных
   * - username
     - имя пользователя для подключения к базе данных
   * - password
     - пароль пользователя
   * - dbname
     - название базы данных биллинга
   * - kernel секция
     -
   * - ip
     - на каком IP будет запущено ядро
   * - port
     - на каком порту ядро будет слушать запросы от radius
   * - pid
     - путь где будет создан PID файл ядра
   * - log
     - лог файл для отображения работы ядра
   * - debug
     - режим дебага ядра, значения ``true/false``
   * - debug_log
     - лог файл куда будет записана информация из дебага
   * - request_timing
     - записывает информацию о медленных запросах (в режиме дебага)
   * -
     -
   * - timezone
     - Временная зона
