---
description: 04/08/2020
---

# Another filtering query - 04/08/2020

## Yet, another filtering query

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d'
{
    "query"{
        "bool": {
            "must": {"match": {"genre": "Sci-Fi}},
            "must_not": {"match": {"title": "trek"}},
            "filter": {"range": {"year": {"gte": 2010, "lt": 2015}}}
        }
    }
}'
```

