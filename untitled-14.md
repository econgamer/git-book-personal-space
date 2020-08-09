---
description: 02/08/2020
---

# Pagination - 02/08/2020

## Pagination

Two key parameters are: from & size

With size only:

```text
curl -XGET '127.0.0.1:9200/movies/_search?size=2&pretty'
```

With from & size:

```bash
curl -XGET '127.0.0.1:9200/movies/_search?size=2&from=2&pretty'
```

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"from": 2,
"size": 2,
"query": {"match": {"genre": "Sci-Fi"}}
}'
```

