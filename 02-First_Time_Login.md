<h1>First_Time_Login</h1>

### Step1 : Go to below URL
Make sure your web server(e.g apache2 has default port:80) is hosted on deafult port, since below command will send request to deafult port of web server.<br>
However in case your web server is not hosted on default port then you must use second URL.
```ruby
http://You_Server_Ip_Or_Name/zabbix
http://Your_Server_IP_Or_Name:Port_Number/zabbix
```
### Step 2: Click NEXT and verify below and then again click NEXT
* Dabase Type : MySQL
* Database Host :  localhost
* Database Agent :  0
* Database Name : zabbix
* Store Credentials in : Plain Text
* User : Zabbix
* Password : "Eneter your set Password"

### Step 3: Enter your zabbix server name and click NEXT and again click NEXT and FINISH
* Dabase Type : Shubham_Zabbix_Server

### Step 4: Login with below default credentials amd sign in to your account.
Username: Admin
Password : zabbix

### Step 5: Change Password
* Administration => Users => Admin => Changed Password => Enter Password => Update 
