DBUpdate
###########################################

Модуль используется для обновления структуры базы данных при обновлении билинга

.. include:: ../../includes/ansible_install.rst

Установка модуля
*******************************************

Скачаем архив установщика, разархивируем его:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbdbupdate.tar.gz
  tar zxf mbdbupdate.tar.gz

.. include:: ../../includes/install/modules/remote_billing_modules.rst

.. include:: ../../includes/install/modules/remote_database.rst

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook mbdbupdate.yml

.. include:: ../../footer_links.rst

.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	mbdbupdate/manual_install
