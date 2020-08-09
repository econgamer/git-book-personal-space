---
description: 27/07/2020
---

# Flattened Datatype - 27/07/2020

## To deal with the issue on Mapping Explosions \(ElasticSearch is using dynamic mapping to individual fields\), it offers Flattened Datatype.

Instead of mapping every object's inter-fields, flattened Datatype map the object's as a whole and children it inside the parents field "Flattened"

Feeding data up

```text
curl -XPUT "http://127.0.0.1:9200/demo-default/_doc/1" -d'{
  "message": "[5592:1:0309/123054.737712:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.",
  "fileset": {
    "name": "syslog"
  },
  "process": {
    "name": "org.gnome.Shell.desktop",
    "pid": 3383
  },
  "@timestamp": "2020-03-09T18:00:54.000+05:30",
  "host": {
    "hostname": "bionic",
    "name": "bionic"
  }
}'
```

Get the result

```bash
curl -XGET "http://127.0.0.1:9200/demo-default/_mapping?pretty=true"
```

Search for "demo-default" in es-cluster-state.json to look for the mapping

```bash
curl -XGET "http://127.0.0.1:9200/_cluster/state?pretty=true" >> es-cluster-state.json
```

## Flattened type case

Create a new dataset "demo-flattened"

```bash
curl -XPUT "http://127.0.0.1:9200/demo-flattened"
```

Create a mapping

```bash
curl -XPUT "http://127.0.0.1:9200/demo-flattened/_mapping" -d'{
  "properties": {
    "host": {
      "type": "flattened"
    }
  }
}'
```

Insert data

```bash
curl -XPUT "http://127.0.0.1:9200/demo-flattened/_doc/1" -d'{
  "message": "[5592:1:0309/123054.737712:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.",
  "fileset": {
    "name": "syslog"
  },
  "process": {
    "name": "org.gnome.Shell.desktop",
    "pid": 3383
  },
  "@timestamp": "2020-03-09T18:00:54.000+05:30",
  "host": {
    "hostname": "bionic",
    "name": "bionic"
  }
}'
```

```bash
curl -XGET "http://127.0.0.1:9200/demo-flattened/_mapping?pretty=true"
```

Add some fields into host field:

```bash
curl -XPOST "http://127.0.0.1:9200/demo-flattened/_update/1" -d'{
    "doc" : {
        "host" : {
          "osVersion": "Bionic Beaver",
          "osArchitecture":"x86_64"
        }
    }
}'
```

Test the results by:

1. query -&gt; term -&gt; full keywords
2. query -&gt; term -&gt; keywords

```bash
curl -XGET "http://127.0.0.1:9200/demo-flattened/_search?pretty=true" -d'{
  "query": {
    "term": {
      "host.osVersion": "Bionic Beaver"
    }
  }
}'
```

```bash
curl -XGET "http://127.0.0.1:9200/demo-flattened/_search?pretty=true" -d'{
  "query": {
    "term": {
      "host.osVersion": "Beaver"
    }
  }
}'
```

