## Nginx glossary

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