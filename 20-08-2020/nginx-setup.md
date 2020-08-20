---
description: 20/08/2020
---

# Nginx - Beginner Guide

## Installation:

```bash
$ sudo apt install curl gnupg2 ca-certificates lsb-release
curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
sudo apt-key fingerprint ABF5BD827BD9BF62
sudo apt update
sudo apt install nginx
```

![](../.gitbook/assets/image%20%286%29.png)

#### My nginx config file is located at: `/etc/nginx`

#### Start Nginx:

```
$ sudo nginx
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're done, edit the /etc/nginx/nginx.conf

```bash
$ sudo nano nginx
```

Comment out all the http block and replace them by the followings: 

```bash
http{
    server{
        location /{
            root /home/kali/Desktop/nginx-workshop/www;
        }
        
        location /images/{
            root /home/kali/Desktop/nginx-workshop;
        }
    }
}
```

Reload the server

```bash
sudo nginx -s reload
```

![](../.gitbook/assets/image%20%284%29.png)

### Setting up proxy server:

```bash
server{
    location / {
        proxy_pass http://localhost:8080;
    }
    
    location ~ \.(gif|jpg|jpeg|png)$ {
        root /home/kali/Desktop/nginx-workshop/images;
    }
}

server{
    listen 8080;
    root /home/kali/Desktop/nginx-workshop/proxy;
    
    location /{
    }

}
```

![](../.gitbook/assets/image%20%282%29.png)

### Cheat Sheet

```bash
sudo netstat -tulpn
```

```bash
ps -ax | grep nginx
```

```bash
sudo nginx -s quit
```

### Tutorial: [http://nginx.org/en/docs/beginners\_guide.html](http://nginx.org/en/docs/beginners_guide.html)

