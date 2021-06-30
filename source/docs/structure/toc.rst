Структура биллинга
###########################################

.. code-block:: bash

	/var/bill/
	├── backup
	│   ├── mbadmin
	│   ├── mbcabapi
	│   ├── mbsql
	│   ├── mbcore
	│   ├── mbpaygw
	│   ├── mbcron
	│   └── mbcabinet
	├── mrtg
	├── license
	├── logs
	│   ├── mbadmin
	│   ├── mbcabapi
	│   ├── mbsql
	│   ├── mbcore
	│   ├── mbpaygw
	│   ├── mbcron
	│   └── mbcabinet
	├── mbadmin
	│   ├── chroot
	│   │   ├── production
	│   │   └── testing
	│   ├── production
	│   └── testing
	├── mbcabapi
	│   ├── chroot
	│   │   ├── production
	│   │   └── testing
	│   ├── production
	│   └── testing
	├── mbsql
	│   ├── production
	│   └── testing
	├── mbcore
	│   ├── production
	│   └── testing
	├── mbpaygw
	│   ├── chroot
	│   │   ├── production
	│   │   └── testing
	│   ├── production
	│   └── testing
	├── mbcron
	│   ├── production
	│   └── testing
	├── mbcabinet
	│   ├── chroot
	│   │   ├── production
	│   │   └── testing
	│   ├── production
	│   └── testing


Описание директорий
*******************************************

.. glossary::

    /var/bill
        Домашняя директория биллинга, тут располагаются файлы модулей

    /var/bill/backup
        Директория для бекапов модулей

    /var/bill/mrtg
        Директория для mrtg графиков

    /var/bill/license
        Директория для файлов лицензии биллинга

    /var/bill/logs
        Директория для логов модулей, каждый лог модуля находится в своей директории с названием модуля

    :doc:`/var/bill/mbadmin <mbadmin>`
        Директория модуля админки, имеет chroot среду и production/testing версии модуля

    :doc:`/var/bill/mbcabapi <mbcabapi>`
        Директория модуля API Личного кабинета пользователей, имеет chroot среду и production/testing версии модуля

    :doc:`/var/bill/mbsql <mbsql>`
        Директория модуля обновления структуры базы данных, имеет production/testing версии модуля

    :doc:`/var/bill/mbcore <mbcore>`
        Директория модуля ядра биллинга, имеет production/testing версии модуля

    :doc:`/var/bill/mbpaygw <mbpaygw>`
        Директория модуля приема платежей, имеет chroot среду и production/testing версии модуля

    :doc:`/var/bill/mbcron <mbcron>`
        Директория модуля заданий и выполнения заданий очереди, имеет production/testing версии модуля

    :doc:`/var/bill/mbcabinet <mbcabinet>`
        Директория модуля Личного кабинета пользователей, имеет chroot среду и production/testing версии модуля


.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	database
	mbsql
	mbradius
	mbcore
	mbcron
	mbadmin
	mbpaygw
	mbcabinet
	mbcabapi

.. include:: ../footer_links.rst
