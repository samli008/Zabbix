## config snmp server
```
yum -y install net-snmp

vi /etc/snmp/snmpd.conf
com2sec notConfigUser  default       liyang
view    systemview    included   .1
view    systemview    included   .1.3.6.1.2.1.1
view    systemview    included   .1.3.6.1.2.1.25.1.1

systemctl enable snmpd
systemctl start snmpd
```
## config snmp client on zabbix server
```
yum -y install net-snmp-utils
snmpwalk -v 2c -c liyang 192.168.8.104 .1.3.6.1.4.1.2021.11.11.0 #vmstat cpu
snmpwalk -v 2c -c liyang 192.168.8.104 .1.3.6.1.2.1.25.2.2.0 #free total memory
```
