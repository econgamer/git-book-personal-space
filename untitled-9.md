---
description: 28/7/2020
---

# Dealing with Mapping Exceptions - 28/07/2020

## Creating the mapping

```bash
curl --request PUT 'http://localhost:9200/microservice-logs' \
--data-raw '{
   "mappings": {
       "properties": {
           "timestamp": { "type": "date"  },
           "service": { "type": "keyword" },
           "host_ip": { "type": "ip" },
           "port": { "type": "integer" },
           "message": { "type": "text" }
       }
   }
}'
```

Creating different entities

```bash
#1 - normal case
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \
--data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "XYZ", "host_ip": "10.0.2.15", "port": "15000", "message": "Hello!" }'

#2 - port - string
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \
--data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "XYZ", "host_ip": "10.0.2.15", "port": "NONE", "message": "I am not well!" }'
```

## Updating the mapping

Closing the index, changing the setting and reopening the index

```text
curl --request POST 'http://localhost:9200/microservice-logs/_close'
```

```bash
curl --location --request PUT 'http://localhost:9200/microservice-logs/_settings' \
--data-raw '{
   "index.mapping.ignore_malformed": true
}'
```

```bash
curl --request POST 'http://localhost:9200/microservice-logs/_open'
```

```bash
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \
--data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "XYZ", "host_ip": "10.0.2.15", "port": "NONE", "message": "I am not well!" }'
```

#### Check the result:

```bash
curl 'http://localhost:9200/microservice-logs/_doc/{id}?pretty'
```

### "index.mapping.ignore\_malformed": true =&gt; can't handle JSON object malformed

```bash
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \ --data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "ABC", "host_ip": "10.0.2.15", "port": 12345, "message": {"data": {"received":"here"}}}'
```

### Work around :dynamic mapping will work for you

```bash
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \
--data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "ABC", "host_ip": "10.0.2.15", "port": 12345, "message": "Received...", "payload": {"data": {"received":"here"}}}'
```

#### error:

```bash
curl --request POST 'http://localhost:9200/microservice-logs/_doc?pretty' \
--data-raw '{"timestamp": "2020-04-11T12:34:56.789Z", "service": "ABC", "host_ip": "10.0.2.15", "port": 12345, "message": "Received...", "payload": {"data": {"received": {"even": "more"}}}}'
```

**Checking the result:**

payload field has been created for you by Dynamic mapping

```bash
curl -XGET "http://127.0.0.1:9200/microservice-logs/_mapping?pretty=true"
```

## Huge number of data

Create one thousand entites \(raw data\):

```bash
thousandone_fields_json=$(echo {1..1001..1} | jq -Rn '( input | split(" ") ) as $nums | $nums[] | . as $key | [{key:($key|tostring),value:($key|tonumber)}] | from_entries' | jq -cs 'add')
```

```bash
echo "$thousandone_fields_json"
```

```bash
curl --location --request PUT 'http://localhost:9200/big-objects'
```

```bash
curl --request POST 'http://localhost:9200/big-objeccts/_doc?pretty' \
--data-raw "$thousandone_fields_json"
```

#### Handling\(high memory pressure\):

```bash
curl --location --request PUT 'http://localhost:9200/big-objects/_settings' \
--data-raw '{
"index.mapping.total_fields.limit": 1001
}'
```

