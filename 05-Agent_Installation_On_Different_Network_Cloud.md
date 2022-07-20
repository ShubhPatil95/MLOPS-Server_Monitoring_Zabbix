<h1>Agent Installation On Different Network Like Cloud</h1>

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
Change Hostname from "zabbix server" to "Cloud Server Zabbix" <br>
Change Server and ServerActive from "127.0.0.1" to "IP Address of Zabbix Host".

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

### Step 7 : Open the port 10050. You need to follow steps as per your cloud provider(GCP,AWS) to open port 10050 on your server.
```ruby
sudo ufw allow 10050
```

### Step 8 : Restart the service
```ruby
sudo systemctl status zabbix-agent.service
```

## Step 9 : Wait for 5-10 minutes and check zabbix agent availability(green = connected, red = not connected)
Configuration => Host => Under Hostname => Check Availability

## Step 10 : TroubleShooting
<strong>1. Run below command on your host server to check if host server can access cloud server </strong>
  ```ruby
  telnet CLOUD_SERVER_IP_ADDRESS 10050
  ```
  If result of this command is showing as below, means your host can access cloud server port 10050.
  ```ruby
  Trying CLOUD_SERVER_IP_ADDRESS...
  Connected to CLOUD_SERVER_IP_ADDRESS
  Escape character is '^]'.
  Connection closed by foreign host.
  ```
  However if output is no else then you need to check if port 10050 is correctly open on cloud server(need to follow steps as per your cloud provider e.g GCP, AWS etc).
  
<strong>2. Run below command on cloud server to check if zabbix host is correctly sending request.

  ```ruby
  sudo tail -f /var/log/zabbix/zabbix_agentd.log
  ```
  Here, Your host server may have public IP, and zabbix using public IP to send request to cloud server. However in <strong>step 5</strong> you might have inserted different(local) IP address of your server. <br>
  In that case above command will show output as below.
  ```ruby
 29919:20220720:114942.837 failed to accept an incoming connection: connection from "PUBLIC_IP_ADDRESS_HOST_SERVER" rejected, allowed hosts: "IP_ADDRESS_MENTIONED_IN_STEP-5"
 29920:20220720:115042.492 failed to accept an incoming connection: connection from "PUBLIC_IP_ADDRESS_HOST_SERVER" rejected, allowed hosts: "IP_ADDRESS_MENTIONED_IN_STEP-5"
  ```
 In this case,<strong>REPEAT STEP 5</strong> to replace Server and ServerActive with "PUBLIC_IP_ADDRESS_HOST_SERVER" in zabbix_agentd.conf file
