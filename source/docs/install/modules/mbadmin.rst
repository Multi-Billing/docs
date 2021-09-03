mbadmin
###########################################

Модуль для работы с биллингом, состоит из backend (логика) и frontend (интерфейс) частей

.. include:: ../../includes/ansible_install.rst

Установка модуля
*******************************************

Скачаем архив установщика, разархивируем его:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbadmin.tar.gz
  tar zxf mbadmin.tar.gz

.. include:: ../../includes/install/modules/remote_billing_modules.rst

.. include:: ../../includes/install/modules/remote_database.rst

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook mbadmin.yml


.. include:: ../../footer_links.rst

.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	mbadmin/manual_install
