Файлы конфигурации
*************************************************

Файл **core.pl** содержит переменные ``$host`` и ``$port`` для подключения к ядру биллинга

.. code-block:: perl
  :emphasize-lines: 27,28
  :linenos:

  use strict;
  use vars qw(%RAD_REQUEST %RAD_REPLY %RAD_CHECK);
  use IO::Socket;
  use locale;
  use POSIX;
  use serialize;

  setlocale(LC_ALL, 'C');
  use constant    RLM_MODULE_REJECT=>  0;#  /* immediately reject the request */
  use constant	RLM_MODULE_FAIL=>      1;#  /* module failed, don't reply */
  use constant	RLM_MODULE_OK=>        2;#  /* the module is OK, continue */
  use constant	RLM_MODULE_HANDLED=>   3;#  /* the module handled the request, so stop. */
  use constant	RLM_MODULE_INVALID=>   4;#  /* the module considers the request invalid. */
  use constant	RLM_MODULE_USERLOCK=>  5;#  /* reject the request (user is locked out) */
  use constant	RLM_MODULE_NOTFOUND=>  6;#  /* user not found */
  use constant	RLM_MODULE_NOOP=>      7;#  /* module succeeded without doing anything */
  use constant	RLM_MODULE_UPDATED=>   8;#  /* OK (pairs modified) */
  use constant	RLM_MODULE_NUMCODES=>  9;#  /* How many return codes there are */

  use constant	RADIUS_L_DBG=> 	       0;# /* debug log  */
  use constant	RADIUS_L_AUTH=>	       1;# /* auth log   */
  use constant	RADIUS_L_PROXY=>       2;# /* peroxy log */
  use constant	RADIUS_L_INFO=>        3;# /* info log   */
  use constant	RADIUS_L_ERROR=>       4;# /* error log  */

  # mbkernel daemon IP address and port
  my $host="127.0.0.1";
  my $port="22007";


Файл **sql.conf** содержит переменные ``server``, ``port``, ``login``, ``password``, ``radius_db`` для подключения к базе данных

.. code-block:: ini
  :emphasize-lines: 4-8
  :linenos:

  sql {
	database = "mysql"
	driver = "rlm_sql_${database}"
	server = "127.0.0.1"
	port = 3306
	login = "user_name"
	password = "user_password"
	radius_db = "database_name"

