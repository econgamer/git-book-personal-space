---
description: 22/7/2020
---

# Bulk API - 22/07/2020

## Get the target content, for example, movie data

```text
scp movies.json econgamer@127.0.0.1:/home/econgamer
```

Uploading the json file via Bulk API

```bash
curl -XPUT 127.0.0.1:9200/_bulk?pretty --data-binary @movies.json
```

GET all data back from ElasticSearch

```bash
less curl -XGET 127.0.0.1:9200/movies/_search?pretty
```

