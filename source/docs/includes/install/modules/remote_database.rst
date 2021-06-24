В файле ``config/database.yaml`` изменить параметры **login** и **pass**, указав логи и пароль пользователя с правами root:

.. code-block:: yaml
    :emphasize-lines: 6,10
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
