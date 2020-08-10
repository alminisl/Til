- Install Nginx 
    - `sudo apt-get install nginx`
    - start with `sudo service nginx start`

- Configure NGINX to forward requests to the different applications

``` bash
cd /etc/nginx/sites-available
touch first-nodejs-app
vim first-nodejs-app
```

- Place the following into the file (assuming its running on port 3000)

``` nginx
server {
    listen 0.0.0.0:80;
    server_name first-nodejs-app.com;
    access_log /var/log/nginx/first-nodejs-app.com.log;
    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header HOST $http_host;
        proxy_set_header X-NginX-Proxy true;
        proxy_pass http://127.0.0.1:3000;
        proxy_redirect off;
    }
}
```

- Make a second app 

``` bash
cd /etc/nginx/sites-available
touch second-nodejs-app
vi second-nodejs-app
```

- Place the following (assuming its running on port 5000)

```nginx
server {
    listen 0.0.0.0:80;
    server_name second-nodejs-app.com;
    access_log /var/log/nginx/second-nodejs-app.com.log;
    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header HOST $http_host;
        proxy_set_header X-NginX-Proxy true;
        proxy_pass http://127.0.0.1:5000;
        proxy_redirect off;
    }
}
```

- Now that we have defined the available sites, we can tell NGINX to use the available sites configuations by simply creating corresponding soft links in the sites-enabled directory.

```bash
cd /etc/nginx
sudo ln -s /etc/nginx/sites-available/first-nodejs-app sites-enabled/first-nodejs-app
sudo ln -s /etc/nginx/sites-available/second-nodejs-app sites-enabled/second-nodejs-app
```

- Restart nginx

```bash 
sudo service nginx restart
```

## Nginx specifics

### Starting/stopping NGINX
```
sudo service nginx start
sudo service nginx stop
sudo service nginx restart
```
### Removing NGINX
```
sudo apt-get remove nginx
apt-get purge nginx nginx-common nginx-full
```
### Installing NGINX

```
sudo apt-get nginx-common # If you removed the nginx-common, you will have to reinstall it
sudo apt-get install nginx
```