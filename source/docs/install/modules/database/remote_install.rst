Существующая СУБД
###########################################

Перед началом установки необходимо подготовить сервер c СУБД.

* Настроить/Отключить Firewall
* Запустить СУБД на IP адресе
* Создать в СУБД пользователя с правами root

**Запуск СУБД на IP адресе**
*******************************************

Для запуска СУБД на определенном IP, необходимо в конфигурации в разде **[mysqld]** добавить параметр **bind**

.. code-block:: bash

    [mysqld]
    bind-address=IP_ADDRESS

Замените **IP_ADDRESS** на нужный IP адрес сервера, для запуска на любом IP необходимо указать **0.0.0.0**.

После чего перезапустите СУБД командой:

.. tabs::

   .. tab:: PerconaDB

      .. code-block:: sql

        systemctl restart mysqld

   .. tab:: MySQL

      .. code-block:: sql

        systemctl restart mysqld

   .. tab:: MariaDB

      .. code-block:: sql

        systemctl restart mariadb

После того как СУБД перезапустится, проверьте что она запущена на нужном IP адресе:

.. code-block:: sh

  netstat -nlp | grep 3306

Результатом данной команды будет показано на каком IP запущена СУБД

.. code-block:: sh

  tcp        0      0 IP_ADDRESS:3306          0.0.0.0:*               LISTEN      4848/mysqld


**Создание пользователя с правами root**
*******************************************

Выполните вход в консоль СУБД, после чего можно создавать пользователя:

.. attention:: Замените **USERNAME** и **USER_PASSWORD** на свои значения

.. tabs::

   .. tab:: доступ по IP

      .. code-block:: sql

        CREATE USER 'USERNAME'@'192.168.1.1' IDENTIFIED BY 'USER_PASSWORD' REQUIRE NONE;
        GRANT ALL PRIVILEGES ON *.* TO 'USERNAME'@'192.168.1.1' WITH GRANT OPTION;
        FLUSH PRIVILEGES;

   .. tab:: доступ по Network

      .. code-block:: sql

        CREATE USER 'USERNAME'@'192.168.1.0/255.255.255.0' IDENTIFIED BY 'USER_PASSWORD' REQUIRE NONE;
        GRANT ALL PRIVILEGES ON *.* TO 'USERNAME'@'192.168.1.0/255.255.255.0' WITH GRANT OPTION;
        FLUSH PRIVILEGES;

   .. tab:: доступ из любой сети

      .. code-block:: sql

        CREATE USER 'USERNAME'@'%' IDENTIFIED BY 'USER_PASSWORD' REQUIRE NONE;
        GRANT ALL PRIVILEGES ON *.* TO 'USERNAME'@'%' WITH GRANT OPTION;
        FLUSH PRIVILEGES;

      .. warning:: После всех установок и настройки, настоятельно рекомендуем удалить такого пользователя.


.. include:: ../../../includes/ansible_install.rst

**Установка**
*******************************************

Скачать и распаковать архив установщика:

.. code-block:: bash

  wget http://setup.multi-billing.pro/database.tar.gz
  tar zxf database.tar.gz

.. include:: ../../../includes/install/modules/remote_billing_database.rst

.. include:: ../../../includes/install/modules/remote_database.rst

После чего можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook database.yml

**Информация**
*******************************************

Во время установки будут созданы пользователи:

.. include:: ../../../includes/install/modules/database/created_users.rst

.. include:: ../../../footer_links.rst