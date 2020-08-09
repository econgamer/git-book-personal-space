---
description: 20/7/2020
---

# ElasticSearch - Environment setup - 20/07/2020

## Download and Install Ubuntu Server

links: [https://ubuntu.com/download/server/thank-you?version=20.04&architecture=amd64](https://ubuntu.com/download/server/thank-you?version=20.04&architecture=amd64)

guide: [https://www.elastic.co/guide/en/elasticsearch/reference/7.8/deb.html\#deb-repo](https://www.elastic.co/guide/en/elasticsearch/reference/7.8/deb.html#deb-repo)

course to follow: [https://www.udemy.com/course/elasticsearch-7-and-elastic-stack](https://www.udemy.com/course/elasticsearch-7-and-elastic-stack)

Space we need: 20GB

**Installation steps:**

```bash
> wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
> sudo apt-get install apt-transport-https
> echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" |
sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
> sudo apt-get update && sudo apt-get install elasticsearch
> sudo nano /etc/elasticsearch/elasticsearch.yml
# uncomment  node.name
# network.host to 0.0.0.0
# discovery.seed_hosts to [“127.0.0.1”]
# cluster.initial_master_nodes to [“node-1”]
>
```

## Running EleasticSearch with systemd

```bash
> sudo /bin/systemctl daemon-reload
> sudo /bin/systemctl enable elasticsearch.service
> sudo /bin/systemctl start elasticsearch.service
```

Once you're done, you can check that ElasticSearch is running by:

```bash
curl -H 'Content-Type:application/json' -XGET '127.0.0.1:9200/'
```

## Importing data to test basic search function \(course materials - Shakespeare data\)

```bash
> wget http://xxx/shakes-mapping.json
> curl -H 'Content-Type: application/json' -XPUT 127.0.0.1:9200/shakespeare 
--data-binary @shakes-mapping.json

> wget http://xxx/shakespeare_7.0.json
> curl -H 'Content-Type: application/json' -XPOST
'127.0.0.1:9200/shakespeare/_bulk?pretty' --data-binary
@shakespeare_7.0.json

#Searching the result by typing
>curl -H 'Content-Type: application/json' -XGET
'127.0.0.1:9200/shakespeare/_search?pretty' -d '
{
"query" : {
"match_phrase" : {
"text_entry" : "to be or not to be"
}
}
}
'
```

