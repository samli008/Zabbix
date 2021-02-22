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

ss -nlpu |grep 161
```
## config snmp client on zabbix server
```
yum -y install net-snmp-utils

# vmstat cpu with snmp oid
snmpwalk -v 2c -c liyang 192.168.8.104 .1.3.6.1.4.1.2021.11.11.0

# free total memory with snmp oid
snmpwalk -v 2c -c liyang 192.168.8.104 .1.3.6.1.2.1.25.2.2.0

# DELL idrac type with oid(idrac setup-->network-->service-->SNMP agent)
snmpwalk -v 2c -c public 192.168.6.11 .1.3.6.1.4.1.674.10892.2.1.1.2.0
# service TAG
snmpwalk -v 2c -c public 192.168.6.11 .1.3.6.1.4.1.674.10892.5.1.3.2
# OS type
snmpwalk -v 2c -c public 192.168.6.10 .1.3.6.1.4.1.674.10892.5.1.3.6
```
