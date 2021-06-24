Выделенный сервер
###########################################

.. note:: При установке используется последняя версия Percona DB.

.. attention:: Установщик не изменяет и не отключает firewall/iptables на сервере, обратите на это внимание!

.. include:: ../../../includes/ansible_install.rst

**Установка базы**
*******************************************

Скачать и распаковать архив установщика:

.. code-block:: bash

  wget http://setup.multi-billing.pro/database.tar.gz
  tar zxf database.tar.gz

В файле ``config/database.yaml`` изменить IP на котором нужно запускать базу данных в параметре **bind**:

.. code-block:: yaml
    :emphasize-lines: 3
    :linenos:

    mysql:
      # на каком адресе запускать MySQL
      bind: "127.0.0.1"
      # пользователь с правами root (для создания базы, пользователей)
      # только если модули биллинга устанавливаются на одном сервере с MySQL
      login: "root"
      # пароль от пользователя root
      # если пароль указан, то он будет использоваться при попытке подключения к базе (пользователь должен быть создан заранее)
      # если значение пустое, пароль будет считан с лога установки и сгенерирован новый
      pass: ""
      # название рабочей базы
      database: "bill"
      # название тест базы
      testing: "bill_test"
      # кодировка базы данных
      encoding: "koi8r"
      collation: "koi8r_general_ci"
      # восстановить базу из бекапа
      # пример:
      # backup_file: "/home/database-2020-12-01.sql"
      # работает только если бекап создан с процедурами и без лишних ключей, к примеру:
      # 	mysqldump --single-transaction --routines -u root -pstrongpassword billing > /home/backup/files/database.sql
      backup_file: ""

После чего можно запускать процесс установки:

.. code-block:: sh

  ansible-playbook database.yml

**Информация**
*******************************************

.. note:: Пароль root от СУБД находится в файле /root/mysql.connect

Во время установки будет использоваться стандартный конфиг биллинга для MySQL рассчитаный на **базовую установку**.

.. include:: ../../../includes/install/modules/database/base_config.rst

Будут созданы пользователи и роли:

.. include:: ../../../includes/install/modules/database/created_users.rst

В конце установки будет создан файл ``/var/bill/database_users.info`` с логином и паролем для входа в модуль **mbadmin**, пример:

.. code-block:: sh

    # BEGIN mbadmin web info
    url_production= https://admin.ispnet.demo
    url_testing= https://test.admin.ispnet.demo
    login=admin
    password=vjWoH45t_0_4fOPX
    # END mbadmin web info

Так же будет создан файл ``/var/bill/database_users.info`` с информацией по созданным пользователям, пример:

.. code-block:: sh

    # BEGIN mbadmin database info
    ip=127.0.0.1
    login=mbadmin
    password=vsoty.2G=3CA6FM3
    # END mbadmin database info
    # BEGIN mbstat database info
    ip=127.0.0.1
    login=mbstat
    password==2Lj.D0BO4vqpK1z
    # END mbstat database info
    # BEGIN mbkernel database info
    ip=127.0.0.1
    login=mbkernel
    password=On=H=P33ahGbGm34
    # END mbkernel database info
    # BEGIN mbradius database info
    ip=127.0.0.1
    login=mbradius
    password=KuByR60=kvJ9Y4x=
    # END mbradius database info
    # BEGIN mbpayments database info
    ip=127.0.0.1
    login=mbpayments
    password=w=2E9dxX3_liMJ1R
    # END mbpayments database info
    # BEGIN mbqueue database info
    ip=127.0.0.1
    login=mbqueue
    password=Y_s_t202yjIu4SVT
    # END mbqueue database info
    # BEGIN mbdbupdate database info
    ip=127.0.0.1
    login=mbdbupdate
    password=zEwi8OG-1U2wx9_W
    # END mbdbupdate database info
    # BEGIN mbcabapi database info
    ip=127.0.0.1
    login=mbcabapi
    password=G1Qv5ZuO==1Vnm2n
    # END mbcabapi database info

.. include:: ../../../footer_links.rst
