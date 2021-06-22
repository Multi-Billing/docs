DBUpdate
###########################################

Модуль используется для обновления структуры базы данных при обновлении билинга

Файловая структура модуля
*******************************************

.. code-block:: bash

	/var/bill
	├── mbdbupdate
	│   ├── production
	│   │   ├── config
	│   │   │   └── config.xml
	│   │   ├── install_update.sh
	│   │   ├── logs
	│   │   │   └── update.log
	│   │   ├── mbdbupdate.current.checksum
	│   │   ├── mbdbupdate.downloaded.checksum
	│   │   ├── mbdbupdate_update.sh
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
	│       ├── mbdbupdate.current.checksum
	│       ├── mbdbupdate.downloaded.checksum
	│       ├── mbdbupdate_testing.sh
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
	│   ├── mbdbupdate
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
   * - /var/bill/mbdbupdate
     - домашняя директория модуля
   * - /var/bill/mbdbupdate/production
     - production версия модуля
   * - /var/bill/mbdbupdate/testing
     - testing версия модуля
   * - <version>/logs
     - директория логов (подключена из /var/bill/logs/mbdbupdate)
   * - <version>/sqlupd
     - директория с файлами обновления базы
   * - <version>/config/config.xml
     - файл конфига модуля
   * - <version>/install_update.sh
     - установщик изменений базы
   * - <version>/mbdbupdate_update.sh
     - загрузщик обновлений базы
   * - <version>/mbdbupdate.current.checksum
     - файл с md5 суммой текущей версии обновлений
   * - <version>/mbdbupdate.downloaded.checksum
     - файл с md5 суммой загруженной версии обновлений 


.. include:: ../includes/config/mbdbpdate.rst
.. include:: ../includes/updates/mbdbpdate.rst
.. include:: ../includes/cron/mbdbpdate.rst
.. include:: ../footer_links.rst