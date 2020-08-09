---
description: 23/7/2020
---

# ElasticSearch - Delete - 23/07/2020

Query the target that will be deleted later

```bash
curl -XGET 127.0.0.1:9200/movies/_search?q=Dark
```

Finding out the id number of the retrieved result is 58559

## Delete Command:

```text
curl -XDELETE 127.0.0.1:9200/movies/_doc/58559
```

Done

