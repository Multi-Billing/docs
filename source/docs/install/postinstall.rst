Действия после установки
###########################################

* Проверка Firewall
* Настройка A записей в DNS
* Авторизация в интерфейсе админки


**Проверка Firewall**
*******************************************

Пример настроенного Firewall:

.. code-block:: sh

    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80
    0     0 ACCEPT     tcp  --  eth2   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443
    0     0 ACCEPT     udp  --  eth1   *       10.10.10.5           0.0.0.0/0           multiport dports 1812,1813
    0     0 ACCEPT     udp  --  eth1   *       10.10.10.15          0.0.0.0/0           multiport dports 1812,1813
    0     0 ACCEPT     udp  --  eth1   *       10.10.10.25          0.0.0.0/0           multiport dports 1812,1813
    0     0 ACCEPT     udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpt:67
    0     0 ACCEPT     tcp  --  eth0   *       217.117.64.232       0.0.0.0/0           tcp dpt:88
    0     0 ACCEPT     tcp  --  eth0   *       217.117.68.232       0.0.0.0/0           tcp dpt:88
    0     0 ACCEPT     tcp  --  *      *       91.226.42.1          0.0.0.0/0           tcp dpt:22
    0     0 DROP       all  --  *      *       0.0.0.0/0

В данном примере используются следующие правила:

* eth0 - интерфейс смотрящий в "мир"
* eth1 - интерфейс в сторону сети с NAS и абонентами
* eth2 - интерфейс в сторону офисной сети
* 10.10.10.x - внутреняя сеть
* 217.117.64.232 - IP платежной системы
* 217.117.68.232 - IP платежной системы

.. code-block:: sh

    # Разрешить localhost
    iptables -A INPUT -i lo -j ACCEPT
    # Разрешаем текущие соединения и созданные сервером (исходящие)
    iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
    # Разрешаем ЛК
    iptables -A INPUT -i eth1 -p tcp --dport 80 -j ACCEPT
    # Разрешаем обращение к админке
    iptables -A INPUT -i eth2 -p tcp --dport 443 -j ACCEPT
    # Разрешаем радиус трафик с NAS
    iptables -A INPUT -i eth1 -s 10.10.10.5 -p udp --match multiport --dports 1812,1813 -j ACCEPT
    iptables -A INPUT -i eth1 -s 10.10.10.15 -p udp --match multiport --dports 1812,1813 -j ACCEPT
    iptables -A INPUT -i eth1 -s 10.10.10.25 -p udp --match multiport --dports 1812,1813 -j ACCEPT
    # Разрешаем dhcp трафик на определенном интерфейсе (если необходимо)
    iptables -A INPUT -i eth1 -i eth0 -p udp --dport 67 -j ACCEPT
    # Разрешаем обращение на платежный шлюз (только с IP платежной системы 217.117.64.232)
    iptables -A INPUT -i eth0 -s 217.117.64.232 -p tcp --dport 88 -j ACCEPT
    iptables -A INPUT -i eth0 -s 217.117.68.232 -p tcp --dport 88 -j ACCEPT
    # Доступ к SSH по IP
    iptables -A INPUT -s 91.226.42.1 -p tcp --dport 22 -j ACCEPT
    # Запрещаем всё остальное
    iptables -A INPUT -j DROP


**DNS записи**
*******************************************

Необходимо добавить DNS записи для субдоменов:

* admin.ispnet.demo - админка биллинга
* test.admin.ispnet.demo - тестовая админка биллинга
* stat.ispnet.demo - личный кабинет абонентов
* test.stat.ispnet.demo - тестовый личный кабинет абонентов
* payments.ispnet.demo - шлюз для приема платежей
* test.payments.ispnet.demo - тестовый шлюз для приема платежей

ispnet.demo - домен "по умолчанию" при установке, если его не меняли при установке, то нужно поменять домены в настойках хостов Nginx.


**Авторизация в админке**
*******************************************

Админку можно открыть по домену (если настраивали) либо по IP адресу сервера через https протокол.

При первом входе вас попросят изменить пароль.