<h1>Agent Installation On Same Network</h1>

### Step 1 : Go to below link and select the appropriate selections.(make sure your are using same version which used for zabbix server)
[Zabbix Agent Installation](https://www.zabbix.com/download?zabbix=6.0&os_distribution=ubuntu&os_version=20.04_focal&db=mysql&ws=apache)

### Step 2 : Further, run a all 3 commands mentioned in 2-Install and configure Zabbix server for your platform on server where you want to install agent

### Step 3 : Now run below command and install zabbix-agent.
```ruby
apt install zabbix-agent
```
### Step 4 : Check zabbix-agent.service status(should be active)
```ruby
systemctl status zabbix-agent.service
```
### Step 5 : Configure HOSTNAME and ServerActive,Server in config file
```ruby
nano /etc/zabbix/zabbix_agentd.conf 
```
Change Hostname from "zabbix server" to "New Server Zabbix" <br>
Change Server and ServerActive from "127.0.0.1" to "IP Address of Zabbix Host"

### Step 6 : Now configure zabbix agent on zabbix server<br>
Configuration =>Host => Create Host(top right)<br>
Enter Hostname : as mentioned in zabbix agent config file <br>
Select Templates => Templates/Operating System => Linux by zabbix agent
Groups : Linux Servers
Interfaces => Add => Agent => Enter IP Address of Agent server => connect to => IP =>Port : 10050 => Add <br>
How to check IP Addrees?
```ruby
ifconfig
```
Now pick IP address mentioned in block "flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500"

### Step 7 : Open the port 10050.
```ruby
sudo ufw allow 10050
```

### Step 8 : Restart the service
```ruby
sudo systemctl status zabbix-agent.service
```

## Step 9 : Wait for 5-10 minutes and check zabbix agent availability(green = connected, red = not connected)
Configuration => Host => Under Hostname => Check Availability








