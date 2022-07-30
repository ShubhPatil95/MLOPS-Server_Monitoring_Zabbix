<h1>Zabbix Installation</h1>

### Step 1 : Go to zabbix website and download the zabbix as per your OS version.
[Zabbix Download Link](https://www.zabbix.com/download?zabbix=6.0&os_distribution=ubuntu&os_version=20.04_focal&db=mysql&ws=apache)

### Step 2 : Run all 4 command show in step 2 under a. Install Zabbix repository and b. Install Zabbix server, frontend, agent on installation page.
* 2 Install and configure Zabbix server for your platform 


### Step 3 : Check the status of the server and agent.
```ruby
sudo service zabbix-server status ## it will show inactive, fine for now
```
```ruby
sudo service zabbix-agent status
```
### Step 4 : Create the Initial Database
* Check if already installed mysql
```ruby
sudo service mysql status
```
* If not installed then run below command check again if it is installed.
```ruby
sudo apt install mysql-server
```
```ruby
sudo service mysql status
```
* Further Run below command to login to mysql
```ruby
sudo mysql -u root -p
```
* Now create a database for zabbix, make sure to replace 'password' with your password
```ruby
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> quit;
```
* Now run below command and enter password you just created.
```ruby
zcat /usr/share/doc/zabbix-sql-scripts/mysql/server.sql.gz | mysql -uzabbix -p zabbix
```
### Step 5 : Configure password in zabbix_server.conf
```ruby
sudo nano /etc/zabbix/zabbix_server.conf
DBPassword= Enter your DB password
```
### step 6 : Start Zabbix server and agent processes
```ruby
sudo systemctl restart zabbix-server zabbix-agent apache2
sudo systemctl enable zabbix-server zabbix-agent apache2
```
### step 7: Restart the apache server
```ruby
sudo service apache2 restart
```
### Step 8 : Check the status of the server and agent.
```ruby
sudo service zabbix-server status ## it will show inactive, fine for now
```
```ruby
sudo service zabbix-agent status
```
