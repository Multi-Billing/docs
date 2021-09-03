Установка на Debian 10
###########################################

В процессе будут установлены следующие основные пакеты вместе с их зависимостями:

* PerconaDB 8.0
* Freeradius 3 + DHCP Module
* PHP 7.3
* PHP-FPM
* Nginx
* Unbound

Модули биллинга:

* :doc:`mbadmin <../structure/mbadmin>`
* :doc:`mbcabinet <../structure/mbcabinet>`
* :doc:`mbsql <../structure/mbsql>`
* :doc:`mbcron <../structure/mbcron>`
* :doc:`mbhookpaygw <../structure/mbpaygw>`
* :doc:`mbdaemoncore <../structure/mbcore>`
* :doc:`mbdaemonqueue <../structure/mbqueue>`
* :doc:`mbdaemonfinance <../structure/mbfinance>`
* mbdaemonfiscalization
* mbdaemonmessenger
* mbdaemonnotify
* mbdaemonbot
* mbdaemontv

А так же вспомогательные пакеты вместе с их зависимостями:

.. code-block::

  wget net-tools sudo mrtg php-pear sysstat

**Требования к серверу/ОС**
*******************************************

* Это должна быть чистая ОС на базе `netinst образа <https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-10.10.0-amd64-netinst.iso>`_ .
* Сервер должен соответствовать `минимальным требованиям <http://multi-billing.pro/produkt/mikbill-sys-requirements.html>`_ биллинга.
* При установке OS **НИКОГДА** не ставте галочку возле "Системные часы используют UTC"

**Установка**
*******************************************

Для установки понадобится ``wget`` и ``Ansible`` версии **2.8/2.9**

Добавьте репозиторий в файл ``/etc/apt/sources.list``:

.. code-block:: sh

    deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main

После чего запустите команды:

.. code-block:: sh

    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
    apt update
    apt install ansible wget

Скачаем и распакуем установщик |project|:

.. code-block:: sh

  wget http://setup.multi-billing.pro/multi-billing.tar.gz
  tar zxf multi-billing.tar.gz

Запустим процесс установки:

.. code-block:: sh

  ansible-playbook multi-billing.yml

После установки будет доступна страница управления билингом по введеному IP-адресу или имени хоста.
Для проверки работы служб выполните:
Ядро биллинга:

.. code-block:: sh

  netstat -nlp | grep 22007
  tcp        0      0 127.0.0.1:22007          0.0.0.0:*               LISTEN      4848/php

База данных:

.. code-block:: sh

  netstat -nlp | grep 3306
  tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4586/mysqld

Радиус сервер:

.. code-block:: sh

  netstat -nlp | grep 181[2-3]
  udp        0      0 0.0.0.0:1812            0.0.0.0:*                           4869/radiusd
  udp        0      0 0.0.0.0:1813            0.0.0.0:*                           4869/radiusd
