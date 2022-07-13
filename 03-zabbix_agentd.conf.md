<h1>Zabbix Config File</h1>

* Check if zabbix server and agent services are active.
```ruby
systemctl status zabbix-server.service 
systemctl status zabbix-agent.service 
```
* Check configuration file=> /etc/zabbix/zabbix_agentd.conf
Below are the important things that need to be check
1. Check if HOSTNAME in config file is matching with your hostname in =>administration=>hosts
2. Check if server=IP address of server which you want to track and same is mentioend in hostname in =>administration=>hosts
3. For active checks only => Check if ServerActive=IP address of server which you want to track and same is mentioend in hostname in =>administration=>hosts
4. Go to host ==>administration=>hosts, you will find ITEMS at top row=> these are the command executed by zabbix, these items can be customized as per your choice.


