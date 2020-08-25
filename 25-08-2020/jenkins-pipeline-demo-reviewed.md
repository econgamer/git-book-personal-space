---
description: 25/08/2020
---

# Jenkins - Pipeline demo reviewed

Tutorial: [https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch](https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch)

Source Code: [https://github.com/econgamer/devops\_pipeline\_demo.git](https://github.com/econgamer/devops_pipeline_demo.git)

## We will use Jenkins Docker version at this demo:

Setting up Jenkins: [https://www.jenkins.io/doc/book/installing/](https://www.jenkins.io/doc/book/installing/)

```
docker container run \
  --name jenkins-blueocean \
  --rm \
  --detach \
  --network jenkins \
  --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client \
  --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 \
  --publish 50000:50000 \
  --publish 8180:8180 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  jenkinsci/blueocean
```

docker:dind =&gt; Docker in Docker \(Remember to open the port 8180 for web server, otherwise you cannot access on the host machine\)

```text
sudo docker container run   --name jenkins-docker   --rm   --detach   --privileged   --network jenkins   --network-alias docker   --env DOCKER_TLS_CERTDIR=/certs   --volume jenkins-docker-certs:/certs/client   --volume jenkins-data:/var/jenkins_home   --publish 2376:2376   --publish 8180:8180   docker:dind

```

Executing Jenkins Shell \(using root\):

```text
sudo docker exec -it --user root jenkins-blueocean /bin/sh
```

Install Maven \(temp\)

```text
#(alpine - blueocean)
apk add maven

FROM jenkins/jenkins:lts
# if we want to install via apt
USER root
RUN apt-get update && apt-get install -y maven
# drop back to the regular jenkins user - good practice
USER jenkins
```

Remarks:

Specify custom workspace for seperate jobs.

![](../.gitbook/assets/image%20%289%29.png)

No source code needed for job2 & 3

![](../.gitbook/assets/image%20%288%29.png)

#### Cheat Sheet

```text
 docker stop my_container
```

