## install grafana
```
yum -y localinstall grafana-7.4.2-1.x86_64.rpm
systemctl enable grafana-server
systemctl start grafana-server
ss -nlpt |grep 3000
http://ip:3000  default:admin/admin
```
## install grafana plugin for zabbix
```
grafana-cli plugins list-remote |grep zabbix
grafana-cli plugins install alexanderzobnin-zabbix-app
cd /var/lib/grafana/plugins
tar xzvf alexanderzobnin-zabbix-app.tar
systemctl restart grafana-server
```
