---
description: 03/08/2020
---

# Sorting - 03/08/2020

Query

```text
curl -XGET '127.0.0.1:9200/movies/_Search?sort=year&pretty'
```

## If you need to sort on an analyzed text field, map a keyword copy

"fields" -&gt; "raw" -&gt; "type" is used for keywords sorting \(this is a field that is not analysed\)

```text
curl -XPUT 127.0.0.1:9200/movies/ -d '
{
    "mappings": {
        "properties": {
            "title":{
                "type": "text",
                "fields": {
                    "raw": {
                        "type": "keyword"
                    }
                }
            }
        }
    }
}'
```

{% hint style="info" %}
You cannot change the mapping on an existing index. You have to delete and set up a new mapping. Thus, you should think probably before importing data into your index
{% endhint %}

```text
curl -XDELETE 127.0.0.1:9200/movies
```

```text
curl -XPUT 127.0.0.1:9200/_bulk --data-binary @movies.json
```

Once the setup is complete, you can execute the below query:

```text
curl -XGET '127.0.0.1:9200/movies/_search?sort=title.raw&pretty'
```

