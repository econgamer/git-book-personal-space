---
description: 26/07/2020
---

# Parents and Children - 26/07/2020

## put the series mapping to ElasticSearch

```bash
curl -XPUT 127.0.0.1:9200/series -d '
{
"mappings": {
"properties": {
"film_to_franchise": {
"type": "join",
"relations": {"franchise": "film"}
}
}
}
}'
```

Get the data from the instructor

```bash
wget http://media.sundog-soft.com/es7/series.json
```

Insert the data to ElasticSearch

```bash
curl -XPUT 127.0.0.1:9200/_bulk?pretty --data-binary @series.json
```

Query all the movies that are associated with the "Star War" franchise:

```bash
curl -XGET 127.0.0.1:9200/series/_search?pretty -d'
{
"query": {
"has_parent": {"parent_type": "franchise",
"query": {
"match": {
"title": "Star Wars"
}
}
}
}
}'
```

Find the specified franchise associated with the film:

```bash
curl -XGET 127.0.0.1:9200/series/_search?pretty -d '
{
"query": {
"has_child": {
"type" : "film",
"query" : {
"match": {
"title": "The Force Awakens"
}
}
}
}
}'
```

