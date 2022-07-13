<h1>Create Trigger In Host Based On Item</h1>

### Step 1 : Go to below page
Configuration => Hosts => Click Trigger In Desired Host => Click Create Trigger(Top Right)

### Step 2 : Enter Trigger Name and Operational Data as below and click add
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Trigger1.png" alt="Host Trigger 1">

### Step 3: Select Item
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Trigger2.png" alt="Host Trigger 2">

### Step 4 Choose Item Create In  
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Trigger3.png" alt="Host Trigger 3">

### Step 5: Enter a result condition above which trigger will generate
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Trigger4.png" alt="Host Trigger 4">


### Step 6: Enter a result condition above which trigger will generate
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/Trigger5.png" alt="Host Trigger 5">

### Step 7: Create A service under name Testing.service, which will run below script and keep on restarting.
```ruby
nano test_script.py
--------------------
import time 
for i in range(100):
    print(i)
    ime.sleep(5)
```

### Step 8: Go to Monitoring => Problems => You will see trigger generated as below.
<img src="https://github.com/ShubhPatil95/MLOPS-Server_Monitoring_Zabbix/blob/main/Images/TriggerCheck.png" alt="Host Trigger 6">

