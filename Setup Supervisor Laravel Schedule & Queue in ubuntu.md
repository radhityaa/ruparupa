# Install Supervisor
```
sudo apt install supervisor -y
```
```
sudo systemctl enable supervisor --now
```
```
sudo systemctl status supervisor
```

# Install Laravel Queue
```
sudo nano /etc/supervisor/conf.d/laravel-queue.conf
```
Copy & Paste This Code
```
[program:laravel-queue]
process_name=%(program_name)s_%(process_num)02d
command=php /var/www/html/artisan queue:work --sleep=3 --tries=3 --timeout=90
autostart=true
autorestart=true
stopasgroup=true
killasgroup=true
user=www-data
numprocs=1
redirect_stderr=true
stdout_logfile=/var/www/html/storage/logs/laravel-queue.log
stopwaitsecs=3600
```

# Install Laravel Schedule
```
crontab -e
```
Insert this code in new line, running one 1 minutes as Laravel recommends.
```
* * * * * cd /var/www/html && php artisan schedule:run >> /dev/null 2>&1
```
for list cron
```
crontab -l
```
