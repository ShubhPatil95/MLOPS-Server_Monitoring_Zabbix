<details><summary> <h2> Apache Error-Proxypass <h2> </summary>
 <p>Invalid command 'ProxyPass', perhaps misspelled or defined by a module not included in the ser> 
  
* Run below command to load proxy_http
```ruby
sudo a2enmod proxy_http
```
</p>
</details>

 
 <details><summary> <h2> Problem Showing on dashboard however no email sent <h2> </summary>
 <p>Zabbix is not sending email to users however showing it in dashaboard 
  
* Make sure your triggers are activate through actions
* Go to Configuration=>Actions=>Trigger Actions=> Enable the status of Report problems to Zabbix administrators
```
</p>
</details>
