# mattermost-dockerfile

Install mariadb docker and edit config/config.json.
```
docker exec -it mariadb bash
mysql -u root -p
  
create user 'mmuser'@'%' identified by 'password';
create database mattermost;
grant all privileges on mattermost.* to 'mmuser'@'%';
 
exit
```

```
vim /opt/mattermost/config/config.json

...
"DriverName": "mysql",
"DataSource": "mmuser:password@tcp(mariadb:3306)/mattermost?charset=utf8mb4,utf8&readTimeout=30s&writeTimeout=30s"
...
```
