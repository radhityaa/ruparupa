# Setup VPS Nginx, mysql, phpmyadmin, php
## 1. Install Nginx
```
sudo apt install nginx -y
```

## 2. Install Repository (PPA) PHP And Install Extensions PHP for Laravel
```
sudo apt install software-properties-common -y
```


```
sudo add-apt-repository ppa:ondrej/php
```

```
sudo apt install php8.2-fpm php8.2-common php8.2-dom php8.2-intl php8.2-mysql php8.2-xml php8.2-xmlrpc php8.2-curl php8.2-gd php8.2-imagick php8.2-cli php8.2-dev php8.2-imap php8.2-mbstring php8.2-soap php8.2-zip php8.2-bcmath -y
```

## 3. Install MariaDB And setting account mysql
download and install: https://mariadb.org/download/?t=repo-config&d=20.04+%22focal%22&v=11.4&r_m=nus

```
sudo su
mysql_secure_installation
```

## 4. Install Phpmyadmin
phpmyadmin, get link download ext.tar.gz (v. english): https://www.phpmyadmin.net/downloads/ 

```
wget -c <url>
```


```
tar xzvf <filename>
```


```
sudo mv <filename *not tar.gz> /usr/share/phpmyadmin
```

```
ln -s /usr/share/phpmyadmin /var/www/html
```


```
	cd /etc/nginx/sites-available
	nano default
```

	add index.php and add location: 

```
	location ~ \.php$ {
		try_files $fastcgi_script_name = 404;
		include fastcgi_params;
		fastcgi_pass unix:/run/php/php8.2-fpm.sock;
		fastcgi_param DOCUMENT_ROOT $realpath_root;
		fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
	} 
```
	(ctrl+o & ctrl+x) 
```
	nginx -t
	systemctl restart nginx
```

## 5. Install Composer
```
sudo apt install composer -y
```

# Create New Website
## 1. create new domain
```/var/www
mkdir sitename.com
```

```
git clone <url>
```

## 2. add script server nginx
```
https://laravel.com/docs/10.x/deployment
```
```
nano /etc/nginx/sites-available/<sitename>
ln -s /etc/nginx/sites-available/<sitename> /etc/nginx/sites-enabled/
nginx -t
systemctl restart nginx
```
```
composer install --optimize-autoloader --no-dev
```

# Add Permission in project laravel:
```
sudo chown -R www-data:www-data /var/www/<domain_path>/storage
sudo chown -R www-data:www-data /var/www/<domain_path>/bootstrap/cache
sudo chmod -R 775 /var/www/<domain_path>/storage
sudo chmod -R 775 /var/www/<domain_path>/bootstrap/cache
```

# install SSL if not used cloudflare:
```
sudo apt update
```
```
sudo apt install certbot python3-certbot-nginx
```
```
sudo certbot --nginx -d example.com
```

# Firewall UFW:
- cek status ufw
```
sudo ufw status verbose
```
```
sudo ufw enable
```
```
sudo ufw app list
```
- wajib: (ftp/mysql)
```
sudo ufw allow <appname>
```
```
ex port range: sudo ufw allow port:port/tcp or more
```
```
ex ip address: sudo ufw allow from <ip> (subnet: /xx)
```
```
ex block spesific: sudo ufw deny <appname>
```
```
ex delete port sudo ufw delete allow/deny port:port/tcp or more
```
