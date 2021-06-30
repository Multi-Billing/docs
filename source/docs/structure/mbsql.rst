DBUpdate
###########################################

Модуль используется для обновления структуры базы данных при обновлении билинга

Файловая структура модуля
*******************************************

.. code-block:: bash

	/var/bill
	├── mbsql
	│   ├── production
	│   │   ├── config
	│   │   │   └── config.xml
	│   │   ├── install_update.sh
	│   │   ├── logs
	│   │   │   └── update.log
	│   │   ├── mbsql.current.checksum
	│   │   ├── mbsql.downloaded.checksum
	│   │   ├── mbsql_update.sh
	│   │   └── sqlupd
	│   │       ├── db
	│   │       │   └── deltas
	│   │       │       ├── 100-2.9.3.sql
	│   │       │       ├─ ...
	│   │       │       └── 99-2.9.2.sql
	│   │       ├── deploy
	│   │       │   ├── build.properties
	│   │       │   ├── build.xml
	│   │       │   └── scripts
	│   │       │       ├── deploy-201809131739.sql
	│   │       │       └── undo-201809131739.sql
	│   │       ├── library
	│   │       └── public
	│   └── testing
	│       ├── config
	│       │   └── config.xml
	│       ├── install_update.sh
	│       ├── logs
	│       │   └── update.log
	│       ├── mbsql.current.checksum
	│       ├── mbsql.downloaded.checksum
	│       ├── mbsql_testing.sh
	│       └── sqlupd
	│           ├── db
	│           │   └── deltas
	│           │       ├── 100-2.9.3.sql
	│           │       ├─ ...
	│           │       └── 99-2.9.2.sql
	│           ├── deploy
	│           │   ├── build.properties
	│           │   ├── build.xml
	│           │   └── scripts
	│           │       ├── deploy-201809131739.sql
	│           │       └── undo-201809131739.sql
	│           ├── library
	│           └── public
	├── logs
	│   ├── mbsql
	│   │   └── update.log

Описание директорий и файлов
*************************************************

.. list-table:: 
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /var/bill
     - домашняя директория биллинга
   * - /var/bill/mbsql
     - домашняя директория модуля
   * - /var/bill/mbsql/production
     - production версия модуля
   * - /var/bill/mbsql/testing
     - testing версия модуля
   * - <version>/logs
     - директория логов (подключена из /var/bill/logs/mbsql)
   * - <version>/sqlupd
     - директория с файлами обновления базы
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/install_update.sh
     - установщик изменений базы
   * - <version>/mbsql_update.sh
     - загрузщик обновлений базы
   * - <version>/mbsql.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/mbsql.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений 


.. include:: ../includes/config/mbsql.rst
.. include:: ../includes/updates/mbsql.rst
.. include:: ../includes/cron/mbsql.rst
.. include:: ../footer_links.rst