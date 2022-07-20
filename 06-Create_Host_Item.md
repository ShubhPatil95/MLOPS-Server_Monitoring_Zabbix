<h1>Create Items In Host</h1>

### Step 1 : Go to below page
Configuration => Hosts => Click Items In Desired Host => Click Create Item(Top Right)

### Step 2 : Enter Details as below.
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/item.png" alt="Host Item">

Kindly make sure that in config file below two lines are mentioned just above <strong>### Option: EnableRemoteCommands</strong> <br>
If not, then add these lines and restart zabbix-agent on that server.
```ruby
nano /etc/zabbix/zabbix_agentd.conf 
```
DenyKey=system.run[] <br>
AllowKey=system.run[*]
```ruby
systemctl restart zabbix-agent.service
````

### Step 3 : Test the Item and Add it

### Step 4: Create A service under name Testing.service, which will run below script and keep on restarting.
```ruby
nano test_script.py
--------------------
import time 
for i in range(100):
    print(i)
    ime.sleep(5)
```

### Step 5: Go to Monitoring => Latest data => Select Hosts(Here it is Zabbix Server) => Name (Service Restart Count) => You will see Item and its last value as below.
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Check%20Item%20Value.png" alt="Host Item value Check">


