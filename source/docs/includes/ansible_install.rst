**Установка ansible**
*******************************************

.. tabs::

   .. tab:: Centos 8

      .. code-block:: sh

          dnf -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
          dnf install --enablerepo epel-playground ansible

   .. tab:: Debian 10

      Добавьте репозиторий в файл ``/etc/apt/sources.list``:

      .. code-block:: sh

        deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main

      После чего запустите команды:

      .. code-block:: sh

        apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
        apt update
        apt install ansible
