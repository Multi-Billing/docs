Файл конфигурации
*************************************************

Файл расположен по пути ``/var/bill/mbdbupdate/<version>/config/config.xml``

.. code-block:: xml

	<config>
	  <parameters>
	    <mysql>
	      <host>DATABASE_IP</host>
	      <username>DATABASE_USER</username>
	      <password>DATABASE_PASSWORD</password>
	      <dbname>DATABASE_NAME</dbname>
	    </mysql>
	  </parameters>
	</config>

.. list-table::
   :widths: 100 100
   :header-rows: 1

   * - параметр
     - описание
   * - host
     - IP адрес базы данных
   * - username
     - имя пользователя для подключения к базе данных
   * - password
     - пароль пользователя
   * - dbname
     - название базы данных биллинга