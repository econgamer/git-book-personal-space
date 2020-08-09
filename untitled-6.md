---
description: 25/7/2020
---

# Analyzers and Tokenizers - 25/07/2020

Execute the below query

```text
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"match": {
"title": "Star Trek"
}
}
}'
```

StarWar and Star Trek will return as a result due to analyzers field\(star match\) and "max\_score" return with it.

```text
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
"query": {
"match_phrase": {
"genre": "sci"
}
}
}'
```

As expected, all genre "Sci-Fi" movies are returned

I want my genre to be well defined, how can I achieve this?

```bash
curl -XDELETE 127.0.0.1:9200/movies
#remove the entire indexs
```

```bash
# recreating movie's mapping
curl -XPUT 127.0.0.1:9200/movies -d '
{
"mappings":{
"properties":{
"id": {"type": "integer"},
"year": {"type": "date"},
"genre": {"type": "keyword"},
"title": {"type": "text", "analyzer": "english"}
}
}
}
}'
```

```bash
curl -XPUT 127.0.0.1:9200/_bulk?prretty --data-binary @movies.json
```

Let's try the above query again and different result will be returned

