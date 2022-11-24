<h1> Auto restart Service through zabbix using python script </h1>

<p>
  
### Step 1: Go to zabbix scrtipts directory.

```ruby
cd /home/zabbix
```

### Step 2: Create a python file service-exit-restart.py 

```ruby
nano service-exit-restart.py
```
### Step 3: Paste below code into service-exit-restart.py  file.

```ruby
import subprocess as sp
import os

substate = sp.getoutput("systemctl show -p SubState --value ServiceName.service")

if substate == "dead":
    os.system("echo 'SudoPassword@123' | sudo -S systemctl restart ServiceName.service")
print(substate)
```
### Step 4: Save it, and give it execute permissions.

```ruby
sudo chmod a+x service-exit-restart.py
```
### Step 5: Run below command to give sudo permission to user : zabbix

```ruby
sudo visudo
```
### Step 6: At the bottom of that file write below line

```ruby
zabbix ALL=(ALL) NOPASSWD:ALL
```

### Step 7:  Go to Zabbix Web UI => Configuration => Host => Item => Create Item with below command.

```ruby
system.run[python3 /home/zabbix/service-exit-restart.py]
```

### Step 8 : Click Test button to validate if its working
</p>
