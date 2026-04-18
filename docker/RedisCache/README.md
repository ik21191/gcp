## RedisCache using docker-compose
- Go to `rediscache-docker-compose` folder and run below command to run the RedisCache docker container.

```
docker-compose up -d
```

**Note:-** Do not run above command again, instead use below commands to `stop` and `start`.

**Stop:** Run `docker-compose stop`

**Start:** Run `docker-compose start`

### Essential Operations
**services:** Defines the services that make up your app. Here, we're defining a service named cache. You would also add other services here, like a database, a web server, etc.

**image:** Tells Docker Compose to use the `Redis 7.4` image based on Alpine Linux.

**restart:** Set to always, which means the container will restart if it stops or crashes.

**ports:** Maps port `6379` on your local machine to port `6379` in the container, allowing you to connect to `Redis` from your host machine.

**command:** Customizes the Redis server command. `--save 20 1` tells Redis to save the database every 20 seconds if at least one change was made. 
`--loglevel` warning sets the logging to show only warnings. `--requirepass` yourpassword sets a password for Redis, which is a basic security measure. Replace yourpassword with a strong password.

**volumes:** Configures a volume named cache and maps it to `/data` inside the container. This ensures that data is persisted even if the container is deleted or recreated.

### Verify Redis is Running
Use below command to enter Redis CLI

```
docker-compose exec cache redis-cli -a mypass@321
```

### Some userful commands
**Set key** `SET testkey "Hello, Redis!"`

**Get key** `GET testkey`

**Get all keys** `keys *`
