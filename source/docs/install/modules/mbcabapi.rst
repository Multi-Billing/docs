mbcabinetAPI
###########################################

Модуль API Личного кабинета

.. include:: ../../includes/ansible_install.rst

Установка модуля
*******************************************

Скачаем архив установщика, разархивируем его:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbcabapi.tar.gz
  tar zxf mbcabapi.tar.gz

.. include:: ../../includes/install/modules/remote_billing_modules.rst

.. include:: ../../includes/install/modules/remote_database.rst

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook mbcabapi.yml


.. include:: ../../footer_links.rst

.. toctree::
	:hidden:
	:maxdepth: 5
	:titlesonly:

	mbcabapi/manual_install
