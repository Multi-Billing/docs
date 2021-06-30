.. container:: toggle

    .. container:: header

        .. raw:: html

            <button>Show/Hide Users</button>


    **mbadmin**
        Используется для модуля админки, имеет свою роль role_mbadmin с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbadmin'

    **mbradius**
        Используется для модуля радиуса, имеет свою роль role_mbradius с правами:

            .. code-block:: sql

                GRANT SELECT ON bill.radnas TO 'role_mbradius'

    **mbcore**
        Используется для модуля ядра билинга, имеет свою роль role_mbcore с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcore'

    **mbpaygw**
        Используется для модуля платежных систем, имеет свою роль role_mbpaygw с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbpaygw'

    **mbcron**
        Используется для модуля очереди, имеет свою роль role_mbcron с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcron'

    **mbcabinet**
        Используется для модуля личного кабинета, имеет свою роль role_mbcabinet с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcabinet'

    **mbcabapi**
        Используется для модуля API личного кабинета, имеет свою роль role_mbcabapi с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcabapi'

    **mbsql**
        Используется для модуля обновления структуры базы биллинга, имеет свою роль mbsql с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbsql'

    .. important:: Указанные наборы привилегий не конечные и могут изменяться с выходом новых обновлений.


.. raw:: html

   <hr>
