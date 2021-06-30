Файл конфигурации
*************************************************

Файл расположен по пути ``/var/bill/mbpaygw/<version>/config/config.xml``

.. code-block:: xml

    <config>
      <parameters>
        <mysql>
          <host>DATABASE_IP</host>
          <username>DATABASE_USER</username>
          <password>DATABASE_PASSWORD</password>
          <dbname>DATABASE_NAME</dbname>
        </mysql>
        <timezone>Europe/Kiev</timezone>
        <partialUTF8>false</partialUTF8>
        <debug>false</debug>
        <error_log>/var/bill/logs/mbadmin.log</error_log>
        <debug_log>/var/bill/logs/mbadmin.debug</debug_log>
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
   * -
     -
   * - timezone
     - Временная зона
   * - partialUTF8
     - Частичное использование UTF8
   * - debug
     - режим дебага, значения ``true/false``
   * - debug_log
     - лог файл куда будет записана информация из дебага
   * - error_log
     - освнойно файл лога
