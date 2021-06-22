MBRadius
###########################################


.. note:: При установке используется последняя версия Freeradius.

.. attention:: Установщик не создаст пользователя для Radius если MySQL расположен на другом сервере. В данном случаи пользователя нужно создавать вручную.

Установка
*******************************************

Скачаем архив установщика, разархивируем его и запустим установку:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbradius.tar.gz
  tar zxf mbradius.tar.gz
  ansible-playbook radius.yml

Установка если база данных на отдельном сервере
*************************************************

Необходимо создать пользователя в базе данных:

.. code-block:: sql

    CREATE USER 'mbradius'@'<IP_ADDRESS>' IDENTIFIED WITH mysql_native_password BY '<USER_PASSWORD>' REQUIRE NONE;
    GRANT 'role_mbradius' TO 'mbradius'@'<IP_ADDRESS>';
    SET DEFAULT ROLE 'role_mbradius' TO 'mbradius'@'<IP_ADDRESS>';
    FLUSH PRIVILEGES;

.. attention:: Замените <IP_ADDRESS> на адрес сервера с которого будет идти подключение к базе данных и <USER_PASSWORD> на пароль для подключения.

Далее скачать и разархивировать архив установщика

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbradius.tar.gz
  tar zxf mbradius.tar.gz

Указать IP адрес сервера базы данных в конфиге: ``config/database.yaml``

.. code-block:: yaml
  :emphasize-lines: 3,3
  :linenos:
  
  # адрес подключения к MySQL (для конфигов модулей биллинга)
  # если указан не 127.0.0.1, то считается что MySQL на отдельном сервере
  host: "127.0.0.1"


Указать пароль пользователя от базы данных в конфиге: ``config/modules/mbradius.yaml``

.. code-block:: yaml
  :emphasize-lines: 6-9
  :linenos:
  
  mbradius:
    software:
      database:
        mysql_user: "mbradius"
        mysql_role: "role_mbradius"
        # Пароль пользователя
        # если пароль указан, то он будет использоваться при попытке подключения к базе (пользователь должен быть создан заранее)
        # если значение пустое, пароль будет сгенерирован (если база данных на одном сервере с модулем)
        mysql_pass: ""

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook radius.yml


Troubleshooting
*******************************************

Для отладки используется запуск Radius из консоли в режиме дебага:

.. code-block:: bash
	
	radiusd -X

Если Radius не может подключиться к MySQL серверу (ниже лог из дебага):

.. code-block:: bash

	rlm_sql (sql): Opening additional connection (0), 1 of 10 pending slots used
	rlm_sql_mysql: Starting connect to MySQL server
	rlm_sql_mysql: Couldn't connect to MySQL server mbradius@192.168.1.177:billing
	rlm_sql_mysql: MySQL error: Can't connect to MySQL server on '192.168.1.177' (115)
	rlm_sql_mysql: Socket destructor called, closing socket
	rlm_sql (sql): Opening connection failed (0)
	rlm_sql (sql): Removing connection pool
	/etc/raddb/sql.conf[1]: Instantiation failed for module "sql"

Возможные варианты решения:

1.
    Проверить при помощи команы ping доступность сервера MySQL с сервера Radius
2.
	Проверить Firewall/Iptables на сервере MySQL
3.
	Проверить что пользователь в MySQL создан и в нем указан нужный IP сервера Radius

.. include:: ../../footer_links.rst