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

    **mbkernel**
        Используется для модуля ядра билинга, имеет свою роль role_mbkernel с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbkernel'

    **mbpayments**
        Используется для модуля платежных систем, имеет свою роль role_mbpayments с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbpayments'

    **mbqueue**
        Используется для модуля очереди, имеет свою роль role_mbqueue с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbqueue'

    **mbstat**
        Используется для модуля личного кабинета, имеет свою роль role_mbstat с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbstat'

    **mbcabapi**
        Используется для модуля API личного кабинета, имеет свою роль role_mbcabapi с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbcabapi'

    **mbdbupdate**
        Используется для модуля обновления структуры базы биллинга, имеет свою роль mbdbupdate с правами:

            .. code-block:: sql

                GRANT ALL PRIVILEGES ON bill.* TO 'role_mbdbupdate'

    .. important:: Указанные наборы привилегий не конечные и могут изменяться с выходом новых обновлений.


.. raw:: html

   <hr>
