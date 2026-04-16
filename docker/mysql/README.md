## MySQL using docker-compose
- Go to `mysql-docker-compose` folder and run below command to run the mysql docker container.

```
docker-compose up -d
```

**Note:-** Do not above command again, instead use below commands to `stop` and `start`.

**Stop:** Run `docker-compose stop`

**Start:** Run `docker-compose start`

**Persistence:** The volumes section maps a Docker-managed volume to `/var/lib/mysql` to save your data permanently.

**Automated Setup:** `MYSQL_DATABASE` automatically creates a database on startup.


## Acessing the MySQL Shell

1. Grant all permissions to user `user`
```
docker exec -it mysql_container mysql -uroot -p
```
When prompted for password enter `root`.

2. Use below command to provide all access to user `user`

```
GRANT ALL ON *.* TO 'user'@'%';
FLUSH PRIVILEGES;
```

**Note:-** If you want to give only `create` permission to `user` then use below command.

```
GRANT CREATE ON *.* TO 'user'@'%';
FLUSH PRIVILEGES;
```

3. Now access mysql database with user `user` using below command

```
docker exec -it mysql_container mysql -uuser -p
```
When prompeted for password enter `12345678`.