---
description: 31/7/2020
---

# Phrase Searching - 31/07/2020

## Slope - represents how far you're willing to let a term move to satisfy a phrase \(in either direction\):

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
    "query": {
        "match_phrase": {
            "title": {"query": "star beyond", "slop": 1}
        }
    }
}'
```

{% hint style="info" %}
Example: "hello Ken and Mary" would match "Ken Mary" with a slop of 1
{% endhint %}

Simple Query:

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"match": {
"title": "star wars"
}
}
}'
```

Either the document containing star or wars will return, giving preference to document containing both "star wars"

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
"query": {
"match_phrase": {
"title": "star wars"
}
}
}'
```

Only documents containing exactly terms will be return

```bash
curl -XGET 127.0.0.1:9200/movies/_search?pretty -d '
{
    "query": {
        "match_phrase": {
            "title": {"query": "star beyond", "slop": 1}
        }
    }
}'
```

