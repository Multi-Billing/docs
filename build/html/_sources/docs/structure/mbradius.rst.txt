MBRadius
###########################################

Файловая структура
*******************************************

В разных версиях OS пути отличаются

.. hlist::
   :columns: 1

   * **Centos** путь ``/etc/raddb``
   * **Debian** путь ``/etc/freeradius/v3``


.. code-block:: bash

	/etc/raddb/
	├── core.pl
	├── dictionary
	├── hints
	├── huntgroups
	├── mods-available
	│   └── perl
	├── mods-config
	│   └── perl
	│       └── example.pl
	├── mods-enabled
	├── modules
	│   ├── acct_unique
	│   ├── always
	│   ├── chap
	│   ├── detail
	│   ├── detail.log
	│   ├── expiration
	│   ├── expr
	│   ├── linelog
	│   ├── logintime
	│   ├── mschap
	│   ├── pap
	│   ├── perl
	│   ├── preprocess
	│   ├── radutmp
	│   ├── realm
	│   ├── sradutmp
	│   └── unix
	├── radiusd.conf
	├── serialize.pm
	├── sites-enabled
	│   ├── billing
	│   └── dhcp
	├── sql.conf
	└── sql_queue.conf

Описание директорий и файлов
*************************************************

.. list-table:: 
   :widths: 100 100
   :header-rows: 1

   * - файл/директория
     - описание
   * - /etc/raddb/
     - директория radius
   * - /etc/raddb/core.pl
     - perl модуль для соединения с ядром биллинга
   * - /etc/raddb/dictionary
     - файл словарей (ведет к /usr/share/freeradius/dictionary)
   * - /etc/raddb/hints
     - https://wiki.freeradius.org/config/Hints
   * - /etc/raddb/huntgroups
     - https://wiki.freeradius.org/config/huntgroups
   * - /etc/raddb/mods-available
     - директория доступных модулей radius
   * - /etc/raddb/mods-enabled
     - директория включенных модулей radius
   * - /etc/raddb/mods-config
     - https://networkradius.com/doc/3.0.10/raddb/mods-config/home.html
   * - /etc/raddb/modules
     - текущие модули radius
   * - /etc/raddb/radiusd.conf
     - файл с настройками radius
   * - /etc/raddb/serialize.pm
     - perl модуль для обработки данных
   * - /etc/raddb/sites-enabled
     - директория включенных сервисов radius
   * - /etc/raddb/sites-enabled/billing
     - сервис биллинга
   * - /etc/raddb/sites-enabled/dhcp
     - сервис DHCP
   * - /etc/raddb/sql.conf
     - файл настроек подключения к базе данных
   * - /etc/raddb/sql_queue.conf
     - файл с sql запросами radius к базе данных

.. include:: ../includes/config/mbradius.rst
.. include:: ../footer_links.rst