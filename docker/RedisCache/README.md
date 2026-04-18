## RedisCache using docker-compose
- Go to `rediscache-docker-compose` folder and run below command to run the RedisCache docker container.

```
docker-compose up -d
```

**Note:-** Do not run above command again, instead use below commands to `stop` and `start`.

**Stop:** Run `docker-compose stop`

**Start:** Run `docker-compose start`

### Essential Operations
If you started your container with `MONGO_INITDB_ROOT_USERNAME` and `MONGO_INITDB_ROOT_PASSWORD`, MongoDB automatically enables authentication. 

- Connect `mongosh` by passing these environment variables in your connection command:

```
docker exec -it my_mongodb mongosh -u admin -p 12345678

or [in case above command doesn't work.]

ocker exec -it my_mongodb mongosh -u admin -p 12345678 --authenticationDatabase admin
```
- Now create new user for your use by using below commands.

```
use admin;
db.createUser({user: "testuser",pwd: "mypass123",roles: [{ role: "root", db: "admin" }]});

#use below command to check if above user created
show users; #You must be in the admin database.
```

- Now you can access mongo shell using `testuser` using below command.

```
docker exec -it my_mongodb mongosh -u testuser -p mypass123
```

- Some useful commands
    - **Check version** `db.version();`
    - **List all databases** `show databases;`
        or `show dbs;`
    - **List all the collections** `show collections;`
    - **Create new MongoDB database** `use mydb`
    - **Create a MongoDB document and add a record to it.** 
	    `db.employee.insertOne({name:"Vinay Kumar",email:"vinay@gmail.com"});  //Where db refers to the current database.`

    - **List the records of employee documents.**
        
        `db.employee.find();  or db.employee.find({});`
    - **Use cases of find() method**

        `db.Book.find({bookName : "BCom"})                                     // with exact match`

        `db.Book.find({bookName : {$regex: "Com"}})                            //Partial exact match`

        `db.Book.find({bookName : {$regex: "com", $options : "i"}})            //partial case-insensitive`
    - **To delete a record**
    
        `db.Book.deleteOne({bookName : "BCom"});  		// To delete one record`
        `db.Book.deleteMany({authorName : "Imran"}); 		// To delete multiple record`
        `db.Book.deleteMany({});					// To delete all records` 

**Persist Data:** Always map a volume to `/data/db` inside the container. Without this, your data is lost when the container is deleted.

**External Connection:** Connect from your host machine or tools like `MongoDB Compass` using the connection string: `mongodb://testuser:mypass123@localhost:27017`

**Spring Boot:** You can add below properties in `application.properties` file to connect `MongoDB`.

```
spring.data.mongodb.host=localhost
spring.data.mongodb.port=27017
spring.data.mongodb.username=testuser
spring.data.mongodb.password=mypass123
spring.data.mongodb.database=BookStore
spring.data.mongodb.authentication-database=admin
```