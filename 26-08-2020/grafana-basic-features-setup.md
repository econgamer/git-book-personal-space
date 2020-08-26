---
description: 26/08/2020
---

# Grafana Basic Features Setup

## Tutorial: [https://grafana.com/tutorials/](https://grafana.com/tutorials/)

Downloading the required elements:

how to install docker compose: 

[https://computingforgeeks.com/how-to-install-latest-docker-compose-on-linux/](https://computingforgeeks.com/how-to-install-latest-docker-compose-on-linux/)

EndPoint: [https://pipedream.com/sources/dc\_K0uQn2](https://pipedream.com/sources/dc_K0uQn2)



Everything is ready:

![](../.gitbook/assets/image%20%2827%29.png)

![Setting up Prometheus as data sources for below metrics](../.gitbook/assets/image%20%2819%29.png)

![](../.gitbook/assets/image%20%2821%29.png)

Logging data source

![](../.gitbook/assets/image%20%2828%29.png)

![{filename=&quot;/var/log/tns-app.log&quot;}](../.gitbook/assets/image%20%2826%29.png)

![{filename=&quot;/var/log/tns-app.log&quot;} \|= &quot;error&quot;](../.gitbook/assets/image%20%2831%29.png)

![Custom dashboard - with {{route}} as x-axis](../.gitbook/assets/image%20%2822%29.png)

![Annotations - Loki - error messages](../.gitbook/assets/image%20%2820%29.png)

![My Endpoint \(for Cloud alert\)](../.gitbook/assets/image%20%2818%29.png)

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}

![message will be sent when traffic is larger than 0.2 per second.](../.gitbook/assets/image%20%2824%29.png)

![Error Messages!~](../.gitbook/assets/image%20%2825%29.png)

![Remember to stop the alert after](../.gitbook/assets/image%20%2830%29.png)



