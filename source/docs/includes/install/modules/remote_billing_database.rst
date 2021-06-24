В файле ``config/billing.yaml`` изменить параметры

* **install_percona** изменить на ``false``
* **mysql_server** указать IP сервера СУБД:

.. code-block:: yaml
    :emphasize-lines: 10,13
    :linenos:

    billing:
      # доменное имя для nginx хостов
      # реузльтатом будет
      # админка: admin.ispnet.demo
      # кабинет пользователей: stat.ispnet.demo
      domain: "ispnet.demo"
      # нужно ли ставить базу данных (софт)
      # если указывать false, то база данных уже должна быть установлена
      # желательно в таком случаи указать пароль от root в конфиге database.yaml
      install_percona: true
      # адрес сервера MySQL (для конфигов модулей биллинга)
      # если указан не 127.0.0.1, то считается что MySQL на отдельном сервере
      mysql_server: "127.0.0.1"
      # mysql шаблон для подключения
      mysql_connect: "/root/mysql.connect"
      # адрес серверов обновлений
      update_server: "update.multi-billing.pro"
      testing_server: "current.multi-billing.pro"
      # какие программы добавлять в chroot среду модулей
      chroot_programs: ["sh", "bash", "echo", "date", "ls", "awk", "sed", "grep", "cat", "rm", "command"]
      # данные директории не трогать!
      dirs:
        tmp: "/tmp/bill/install"
        home: "/var/bill"
        logs: "logs"
        backups: "backup"
        files: "files"
        scripts: "scripts"
        custom: "custom"
