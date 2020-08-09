---
description: 01/08/2020
---

# Exercise - querying - 01/08/2020

## Tasks:

Search for "Star Wars" movies released after 1980, using both a URI search and a request body search.

range doc: [https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html)

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"bool": {
"must": {"match_phrase": {"title": "Star Wars"}},
"filter": {"range": {"year": {"gt": 1980}}}
}
}
}'
```

Using query lite \(Remember to do url encode\):

encoding: [https://www.urlencoder.org/](https://www.urlencoder.org/)

```bash
curl -XGET "127.0.0.1:9200/movies/_search?q=+year>1980+title:star%20wars&pretty"
```

```bash
curl -XGET "127.0.0.1:9200/movies/_search?q=%2Byear%3A%3E1980+%2Btitle%3Astar%20wars&pretty"
```

