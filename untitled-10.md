---
description: 29/07/2020
---

# Query Lite - 29/07/2020

## Backsides

* Cryptic and hard to debug
* can be a security issue if exposed to client-side
* Fragile - can be disrupted for any type error

Query a simple entry using keyword search

```text
curl -XGET "127.0.0.1:9200/movies/_search?q=title:star&pretty"
```

More advanced one:

```bash
curl -XGET "127.0.0.1:9200/movies/_search?q=+year>2010+title:trek&pretty"
```

URL encoded version:

```bash
curl -XGET "127.0.0.1:9200/movies/_search?q=%2Byear%3A%3E2010+%2Btitle%3Atrek&pretty"
```

