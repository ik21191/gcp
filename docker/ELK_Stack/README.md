# ELK(Elasticsearch, Logstack and Kibana) Stack for Logging
- Go to `elk-docker-compose` folder and run below command to run all the required applications for this logging stack.

```
docker-compose up -d
```

**Note:-** Do not run above command again, instead use below commands to `stop` and `start`.

**Stop:** Run `docker-compose stop`

**Start:** Run `docker-compose start`

# Elasticsearch

To search all the indices in `Elasticsearch`, hit below end point in the browser.

[elasticsearch](http://localhost:9200/_cat/indices?v)


# Kibana

## To search an index in Kibana
Kibana provides a built-in management interface that does not require writing queries
- Open Kibana
- Search `Stack Management`
- In left side menu go to `Data` section and then click on `Index Management`, it will display all indices which are present in `Elasticsearch` node.

## To create an index pattern which you want to display on `Discover`
- Open Kibana
- Search `Stack Management`
- In left side menu go to `Kibana` section and then click on `Index Patterns`.
- Click on `Create Index Pattern`, it will display all the indices which are present on `Elasticsearch`.
- Then, in `name` text field start typing name of your index.
- It will start searching of your pattern in the right side and finally click on `Create index patter` in the bottom.

## To display your logs
- Search `Discover` in `Elastic Search`.
- In the left side, you can see a drop down of all the available `Elasticsearch` indices.
- Select your index and it will display all the logs for your index.
