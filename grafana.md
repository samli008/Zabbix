## install grafana
```
yum -y localinstall grafana-7.4.2-1.x86_64.rpm
systemctl enable grafana-server
systemctl start grafana-server
ss -nlpt |grep 3000
```
