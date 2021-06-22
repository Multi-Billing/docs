База данных
###########################################

.. note:: При установке используется последняя версия Percona DB.

.. attention:: Установщик не изменяет и не отключает firewall/iptables на сервере, если MySQL будет использоваться на отдельном сервере обратите на это внимание!

**Конфигурация**
*******************************************

Файл конфигурации находится в ./config/database.yaml

.. code-block:: yaml

	mysql:
	  # на каком адресе запускать MySQL
	  bind: "127.0.0.1"
	  # адрес подключения к MySQL (для конфигов модулей биллинга)
	  # если указан не 127.0.0.1, то считается что MySQL на отдельном сервере
	  host: "127.0.0.1"
	  # пользователь с правами root (для создания базы, пользователей)
	  # только если модули биллинга устанавливаются на одном сервере с MySQL
	  login: "root"
	  # пароль от пользователя root
	  # если пароль указан, то он будет использоваться при попытке подключения к базе (пользователь должен быть создан заранее)
	  # если значение пустое, пароль будет считан с лога установки и сгенерирован новый
	  pass: ""
	  # название рабочей базы
	  database: "bill"
	  # название тест базы
	  testing: "bill_test"
	  # кодировка базы данных
	  encoding: "koi8r"
	  collation: "koi8r_general_ci"
	  # восстановить базу из бекапа
	  # пример:
	  # backup_file: "/home/database-2020-12-01.sql"
	  # работает только если бекап создан без лишних ключей, к примеру:
	  # 	mysqldump --single-transaction -u root -pstrongpassword billing > /home/backup/files/database.sql
	  backup_file: ""


**Установка**
*******************************************

Скачать и распаковать архив установщика:

.. code-block:: bash

  wget http://setup.multi-billing.pro/database.tar.gz
  tar zxf database.tar.gz

Если база данных устанавливается на отдельном сервере, необходимо в конфигурации ``config/billing.yaml`` в переменной ``bind`` указать IP адрес на котором будет запущена служба базы данных

После чего можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook database.yml

**Информация**
*******************************************

Во время установки будет использоваться стандартный конфиг биллинга для MySQL рассчитаный на базовую установку.

.. container:: toggle

    .. container:: header

        .. raw:: html

            <button>Show/Hide Config</button>

    .. code-block:: ini

        [client]
        port = 3306
        socket=/var/lib/mysql/mysql.sock

        [mysql]
        loose-local-infile=1

        [mysqld_safe]
        err-log = /var/log/mysql/mysql.err

        [mysqld]
        user = mysql
        port = 3306
        bind-address = 127.0.0.1
        socket = /var/lib/mysql/mysql.sock
        pid-file = /var/run/mysqld/mysqld.pid
        log-error = /var/log/mysql/mysql.err
        basedir = /usr
        datadir = /var/lib/mysql
        skip-external-locking
        #symbolic-links=0
        skip-name-resolve
        default-storage-engine=innodb
        log_bin_trust_function_creators=1
        skip-log-bin
        sync_binlog = 0
        sql-mode=''
        optimizer_switch = 'index_merge=on,index_merge_union=on,index_merge_sort_union=on,index_merge_intersection=on,engine_condition_pushdown=off,index_condition_pushdown=off,mrr=off,mrr_cost_based=off,subquery_materialization_cost_based=off,use_index_extensions=off,condition_fanout_filter=off,derived_merge=off,use_invisible_indexes=off,skip_scan=off,hash_join=off'
        performance_schema = OFF


        #system
        loose-local-infile=1
        open_files_limit = 35000
        #query_cache_size = 256M
        #query_cache_limit = 256M
        join_buffer_size = 256M
        max_join_size=256M
        max_connect_errors = 1K
        max_allowed_packet=16M
        table_open_cache = 4096
        #table_cache = 1k
        max_heap_table_size = 1024M
        tmp_table_size = 1024M
        interactive_timeout = 120
        wait_timeout = 120
        connect_timeout = 120
        thread_cache_size = 32
        #thread_concurrency = 4
        max_connections = 128

        #Myisam
        key_buffer_size = 8M
        sort_buffer_size = 2M
        read_buffer_size = 2M
        read_rnd_buffer_size = 2M
        myisam_sort_buffer_size = 2M


        #ниже включается бинари лог, разкоментируйте следующие 2 строки чтобы включить
        #server-id=1
        #log-bin=mysqld-bin
        tmpdir = /tmp/

        # innodb
        innodb_file_per_table
        innodb_flush_method=O_DIRECT
        innodb_buffer_pool_size = 1372M
        # default is 8 (or 1 if innodb_buffer_pool_size < 1GB)
        innodb_buffer_pool_instances = 4
        #innodb_additional_mem_pool_size = 4M
        innodb_data_home_dir = /var/lib/mysql/
        innodb_log_group_home_dir = /var/lib/mysql/
        innodb_data_file_path = ibdata1:12M:autoextend
        innodb_log_file_size = 256M
        innodb_log_buffer_size = 8M
        innodb_log_files_in_group = 2
        innodb_flush_log_at_trx_commit = 0
        innodb_lock_wait_timeout = 300
        innodb_read_io_threads = 4
        innodb_write_io_threads = 4
        innodb_thread_concurrency = 4


        [mysqldump]
        quick
        max_allowed_packet = 16M

        [isamchk]
        key_buffer = 20M
        sort_buffer_size = 20M
        read_buffer = 2M
        write_buffer = 2M

        [myisamchk]
        key_buffer_size = 256M
        sort_buffer_size = 256M
        read_buffer = 2M
        write_buffer = 2M

        [mysqlhotcopy]
        interactive-timeout

        [mysqld_safe]
        log-error=/var/log/mysql/mysqld.log
        pid-file=/var/run/mysqld/mysqld.pid


.. raw:: html

   <hr>


Так же будут созданы пользователи:

:doc:`mbadmin <mbadmin>`
	Используется для модуля админки, имеет свою роль role_mbadmin с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbadmin'

:doc:`mbradius <mbradius>`
	Используется для модуля радиуса, имеет свою роль role_mbradius с правами:
		
		.. code-block:: sql
		
			GRANT SELECT ON bill.radnas TO 'role_mbradius'

:doc:`mbkernel <mbkernel>`
	Используется для модуля ядра билинга, имеет свою роль role_mbkernel с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbkernel'

:doc:`mbpayments <mbpayments>`
	Используется для модуля платежных систем, имеет свою роль role_mbpayments с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbpayments'

:doc:`mbqueue <mbqueue>`
	Используется для модуля очереди, имеет свою роль role_mbqueue с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbqueue'
			
:doc:`mbstat <mbstat>`
	Используется для модуля личного кабинета, имеет свою роль role_mbstat с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbstat'

:doc:`mbcabapi <mbcabapi>`
	Используется для модуля API личного кабинета, имеет свою роль role_mbcabapi с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcabapi'

:doc:`mbdbupdate <mbdbupdate>`
	Используется для модуля обновления структуры базы биллинга, имеет свою роль mbdbupdate с правами:
		
		.. code-block:: sql
		
			GRANT ALL PRIVILEGES ON bill.* TO 'role_mbdbupdate'

.. important:: Указанные наборы привилегий не конечные и могут изменяться с выходом новых обновлений.


**Troubleshooting**
*******************************************


.. include:: ../../footer_links.rst