---
description: 22/7/2020
---

# ElasticSearch - Versioning - 22/07/2020

Get the entry by GET

```bash
curl -XGET 127.0.0.1:9200/movies/_doc/109487?pretty
```

Update entry via PUT

```bash
curl -XPUT 127.0.0.1:9200/movies/_doc/109487?pretty -d '
{
"genre": ["IMAX", "Sci-Fi"],
"title": "Interstellar foo",
"year": 2014
}'
```

GET the updated entry and notice that the version has been updated

```bash
curl -XGET 127.0.0.1:9200/movies/_doc/109487?pretty
```

Partially update via POST

```bash
curl -XPOST 127.0.0.1:9200/movies/_doc/109487/_update -d '
{
"doc": {
"title": "Interstellar"
}
}'
```

Check the result again

```bash
curl -XGET 127.0.0.1:9200/movies/_doc/109487?pretty
```

