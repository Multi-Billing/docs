Структура биллинга
###########################################

.. code-block:: bash

	/var/bill/
	├── backup
	│   ├── mbadmin
	│   ├── mbcabapi
	│   ├── mbdbupdate
	│   ├── mbkernel
	│   ├── mbpayments
	│   ├── mbqueue
	│   └── mbstat
	├── mrtg
	├── license
	├── logs
	│   ├── mbadmin
	│   ├── mbcabapi
	│   ├── mbdbupdate
	│   ├── mbkernel
	│   ├── mbpayments
	│   ├── mbqueue
	│   └── mbstat
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
	├── mbdbupdate
	│   ├── production
	│   └── testing
	├── mbkernel
	│   ├── production
	│   └── testing
	├── mbpayments
	│   ├── chroot
	│   │   ├── production
	│   │   └── testing
	│   ├── production
	│   └── testing
	├── mbqueue
	│   ├── production
	│   └── testing
	├── mbstat
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

    :doc:`/var/bill/mbdbupdate <mbdbupdate>`
        Директория модуля обновления структуры базы данных, имеет production/testing версии модуля

    :doc:`/var/bill/mbkernel <mbkernel>`
        Директория модуля ядра биллинга, имеет production/testing версии модуля

    :doc:`/var/bill/mbpayments <mbpayments>`
        Директория модуля приема платежей, имеет chroot среду и production/testing версии модуля

    :doc:`/var/bill/mbqueue <mbqueue>`
        Директория модуля заданий и выполнения заданий очереди, имеет production/testing версии модуля

    :doc:`/var/bill/mbstat <mbstat>`
        Директория модуля Личного кабинета пользователей, имеет chroot среду и production/testing версии модуля


.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	database
	mbdbupdate
	mbradius
	mbkernel
	mbqueue
	mbadmin
	mbpayments
	mbstat
	mbcabapi

.. include:: ../footer_links.rst
