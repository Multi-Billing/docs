MBRadius
###########################################

.. note:: При установке используется последняя версия FreeRadius.

.. include:: ../../includes/ansible_install.rst

Установка модуля
*******************************************

Скачаем архив установщика, разархивируем его:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbradius.tar.gz
  tar zxf mbradius.tar.gz

.. include:: ../../includes/install/modules/remote_billing_modules.rst

.. include:: ../../includes/install/modules/remote_database.rst

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

.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	mbradius/manual_install
