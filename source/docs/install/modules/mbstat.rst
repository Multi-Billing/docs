MBStat
###########################################

Модуль личного кабинета абонента

Установка
*******************************************

Скачаем архив установщика, разархивируем его и запустим установку:

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbstat.tar.gz
  tar zxf mbstat.tar.gz
  ansible-playbook mbstat.yml

Установка если база данных на отдельном сервере
*************************************************

Необходимо создать пользователя в базе данных:

.. code-block:: sql

    CREATE USER 'mbstat'@'<IP_ADDRESS>' IDENTIFIED WITH mysql_native_password BY '<USER_PASSWORD>' REQUIRE NONE;
    GRANT 'role_mbstat' TO 'mbstat'@'<IP_ADDRESS>';
    SET DEFAULT ROLE 'role_mbstat' TO 'mbstat'@'<IP_ADDRESS>';
    FLUSH PRIVILEGES;

.. attention:: Замените <IP_ADDRESS> на адрес сервера с которого будет идти подключение к базе данных и <USER_PASSWORD> на пароль для подключения.

Далее скачать и разархивировать архив установщика

.. code-block:: bash

  wget http://setup.multi-billing.pro/mbstat.tar.gz
  tar zxf mbstat.tar.gz

Нужно указать IP адрес сервера MySQL в конфиге: ``config/database.yaml``

.. code-block:: yaml
  :emphasize-lines: 3,3
  :linenos:
  
  # адрес подключения к MySQL (для конфигов модулей биллинга)
  # если указан не 127.0.0.1, то считается что MySQL на отдельном сервере
  host: "127.0.0.1"

Указать пароль пользователя от базы данных в конфиге: ``config/modules/mbstat.yaml``

.. code-block:: yaml
  :emphasize-lines: 6-9
  :linenos:
  
  mbstat:
    software:
      database:
        mysql_user: "mbstat"
        mysql_role: "role_mbstat"
        # Пароль пользователя
        # если пароль указан, то он будет использоваться при попытке подключения к базе (пользователь должен быть создан заранее)
        # если значение пустое, пароль будет сгенерирован (если база данных на одном сервере с модулем)
        mysql_pass: ""

Далее можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook mbstat.yml


.. include:: ../../footer_links.rst