# Nginx Setup

## Installation:

```bash
$ sudo apt install curl gnupg2 ca-certificates lsb-release
curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
sudo apt-key fingerprint ABF5BD827BD9BF62
sudo apt update
sudo apt install nginx
```

![](.gitbook/assets/image%20%283%29.png)

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
            root /home/kali/Desktop/nginx-workshop;
        }
        
        location /images/{
            root /home/kali/Desktop/nginx-workshop/images;
        }
    }
}
```

Reload the server

```bash
sudo nginx -s reload
```

![](.gitbook/assets/image%20%282%29.png)

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

