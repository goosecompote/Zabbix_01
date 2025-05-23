# Домашнее задания "Система мониторинга Zabbix" Павлов Дмитрий

## Задание 1

![скриншот к заданию 1](https://github.com/goosecompote/Zabbix_01/blob/main/pic/pic01.png)

Установка сервера:  

Установите и сконфигурируйте Zabbix для выбранной платформы  
a. Become root user  
Start new shell session with root privileges.  
$ sudo -s  
b. Установите репозиторий Zabbix  
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb  
dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb  
apt update  
c. Установите Zabbix сервер, веб-интерфейс и агент  
apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent  
d. Создайте базу данных  
Установите и запустите сервер базы данных.  
Выполните следующие комманды на хосте, где будет распологаться база данных.  
sudo -u postgres createuser --pwprompt zabbix  
sudo -u postgres createdb -O zabbix zabbix  
На хосте Zabbix сервера импортируйте начальную схему и данные. Вам будет предложено ввести недавно созданный пароль.  
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix  
e. Настройте базу данных для Zabbix сервера  
Отредактируйте файл /etc/zabbix/zabbix_server.conf  
DBPassword=password  
f. Запустите процессы Zabbix сервера и агента  
Запустите процессы Zabbix сервера и агента и настройте их запуск при загрузке ОС.  
systemctl restart zabbix-server zabbix-agent apache2  
systemctl enable zabbix-server zabbix-agent apache2   

## Задание 2

![скриншот к заданию 1](https://github.com/goosecompote/Zabbix_01/blob/main/pic/pic02.png)
![скриншот к заданию 1](https://github.com/goosecompote/Zabbix_01/blob/main/pic/pic03.png)
![скриншот к заданию 1](https://github.com/goosecompote/Zabbix_01/blob/main/pic/pic04.png)


Установка клиента:  

a. Become root user  
Start new shell session with root privileges.  
$ sudo -s  
b. Установите репозиторий Zabbix  
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb  
dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb  
apt update  
c. Установите Zabbix агент  
apt install zabbix-agent  
d. Запустите процесс Zabbix агента  
Запустите процесс Zabbix агента и настройте его запуск при загрузке ОС.  
systemctl restart zabbix-agent  
systemctl enable zabbix-agent  
