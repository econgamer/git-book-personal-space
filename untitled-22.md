---
description: 19/07/2020
---

# kafka - import/export files\(logs\) - 19/07/2020

## Getting the config files ready

Three config files are needed in this case, namely, connect-standalone.

```bash
./connect-standalone.sh ~/test/connect-standalone.properties ~/test/connect-file-source.properties ~/test/connect-file-sink.properties
```

Start the consumer

```bash
> cd /usr/hdp/current/kafka-broker/config
> ./kafka-console-consumer.sh --bootstrap-server sandbox.hortonworks.com:6667 --zookeeper sandbox-hdp.hortonworks.com:2181 --topic test
```

Before running the above execution, place those config files into the right place and edit them

Config files original : **location:** _**/usr/hdp/current/kafka-broker/conf**_

```bash
> cd /usr/hdp/current/kafka-broker/conf
> cp connect-standalone.properties ~/test
> cp connect-file-source.properties ~/test    # Source files
> cp connect-file-sink.properties ~/test    # the location where we wanna to write
```

```bash
> cd ~/test
> nano connect-standalone.properties
# bootstrap.servers=sandbox-hdp.hortonworks.com:6667

> nano connect-file-sink.properties
# file=/home/maria_dev/test/log.txt
# topics=test

> mamo connect-file-source.properties
# file=/home/maria_dev/test/access_log.txt
# topics=test
```

You're freely to insert any text into access\_log.txt by _**"echo "New info" &gt;&gt; access\_log.txt"**_

