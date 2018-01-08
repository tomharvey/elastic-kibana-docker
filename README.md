# Elasticsearch Kibana Dev environment

A running single ES cluster with kibana hooked into it. Uses v6.0.1 of ES and Kibana

This does not use X-Pack for any security, it's meant for local dev environments.


### Docker requirements
Starts through Docker, so install Docker first.

Then configure your docker host to properly handle Elasticsearch.

##### For OSX
```
docker-machine ssh
sudo sysctl -w vm.max_map_count=262144
```
##### For other OSes
See the [notes on increasing the limits here](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-prod-mode)


### Getting started
Run this command to start both elasticsearch and kibana:
```docker-compose up```


### Hostname
If you're running docker on OSX, you're actually using a VM. Add the IP address of that VM to your host file to make it easier to access the services

```echo $(docker-machine ip) dockerhost | sudo tee -a /etc/hosts```

If you're using Linux, you can use `localhost` instead of `dockerhost` in the below URIs

You can now:

* Access ES at http://dockerhost:9200

* Access Kibana at http://dockerhost:5601

* Check the ES cluster status with `curl http://dockerhost:9200/_cat/health`

