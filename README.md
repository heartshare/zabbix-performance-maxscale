# zabbix-performance-maxscale

Installation
------------

```bash
# maxscale user parameters config
<<<<<<< HEAD
sudo curl https://raw.githubusercontent.com/impnumber13/zabbix-performance-maxscale/master/userparameter_maxscale.conf -o /etc/zabbix/zabbix_agentd.d/userparameter_maxscale.conf
```

```bash
# selinux config
sudo ausearch -r -m avc | grep -E 'zabbix|maxctrl' | audit2allow -m zabbix_maxctrl > zabbix_maxctrl.te
sudo checkmodule -M -m -o zabbix_maxctrl.mod zabbix_maxctrl.te
sudo semodule_package -o zabbix_maxctrl.pp -m zabbix_maxctrl.mod
sudo semodule -i zabbix_maxctrl.pp
```

```bash
sudo maxctrl enable account zabbix
sudo systemctl restart zabbix-agent.service
```