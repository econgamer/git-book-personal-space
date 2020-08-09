---
description: 24/7/2020
---

# Race Condition - 24/07/2020

## ElasticSearch is using primary\_term and seq\_no as an indicator for concurrency update

```bash
curl -XGET 127.0.0.1:9200/movies/_doc/109487?pretty
```

Update the document restricting the update to this seq\_no:

```bash
curl -XPUT "127.0.0.1:9200/movies/_doc/109487?if_seq_no&if_primary_term=2" -d '
{
"genres": ["IMAX", "Sci-Fi"],
"title": "Interstellar hello",
"year": 2014
}'
```

{% hint style="info" %}
Version Conflict for one of the update occurs if race-condition happened
{% endhint %}

```bash
curl -XPOST 127.0.0.1:9200/movies/_doc/109487/_update?retry_on_conflict=5 -d'
```

Another method you could use is updated based on retry\_on\_conflict to manage update automatically

