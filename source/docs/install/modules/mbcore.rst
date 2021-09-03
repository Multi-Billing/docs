mbdaemoncore
###########################################

Модуль используется для обработки Freeradius запросов (Access-Request/Accounting-Request) при авторизации абонентов.

.. include:: ../../includes/ansible_install.rst

Установка модуля
*******************************************

Скачаем архив установщика, разархивируем его:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbdaemoncore.tar.gz
  tar zxf mbdaemoncore.tar.gz

.. include:: ../../includes/install/modules/remote_billing_modules.rst

.. include:: ../../includes/install/modules/remote_database.rst

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook mbdaemoncore.yml


.. include:: ../../footer_links.rst

.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	mbcore/manual_install
