## install zabbix 5.0
```
yum -y install zabbix-server-mysql zabbix-agent centos-release-scl zabbix-get
yum -y install zabbix-web-mysql-scl zabbix-apache-conf-scl mariadb-server
systemctl enable --now mariadb
mysql_secure_installation
create database zabbix character set utf8 collate utf8_bin;
grant all privileges on zabbix.* to zabbix@localhost identified by 'liyang';
```
## import zabbix database
```
rpm -ql zabbix-server-mysql | grep sql 
zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -pliyang zabbix
mysql -uroot zabbix -e 'show tables'
```
## setup zabbix server connect mysql
```
vi /etc/zabbix/zabbix_server.conf
DBPassword=liyang
```
