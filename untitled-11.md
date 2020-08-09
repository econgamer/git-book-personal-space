---
description: 30/7/2020
---

# JSON Search Conditioning - 30/07/2020

## Query

The normal one:

```text
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"match": {
"title": "star"
}
}
}'
```

Implement filter into the query:

```text
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"bool": {
"must": {"term": {"title": "trek"}},
"filter": {"range": {"year": {"gte": 2010}}}
}
}
}'
```

