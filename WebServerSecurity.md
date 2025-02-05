## Melihat log Web Server
Apache2
```
cat /var/log/apache2/access.log
```
NGINX
```
cat /var/log/nginx/access.log
```

## Mengamankan Apache dari NMAP
Edit Konfigurasi Apache
```
nano /etc/apache2/apache2.conf
```
Tambahkan di apache2.conf
```
ServerTokens Prod
ServerSignature Off
```
Restart Apache
```
service apache2 restart
```

## Mengamankan NGINX dari NMAP
Edit Konfigurasi NGINX
```
nano /etc/nginx/nginx.conf
```
Tambahkan di nginx.conf
```
server_tokens off;
```
Restart NGINX
```
service nginx restart
```

## Mengamankan PHP dari WebShell
A. Contoh menggunakan Apache2
```
nano /etc/php8.3/apache2/php.ini
```
Tambahkan di php.ini
```
disable_functions = curl_multi_exec, popen, passthru, exec, popen, symlink, proc_open, shell_exec, show_source, allow_url_fopen, system, passthru, parse_ini_file, show_source, exec, proc_open, phpinfo, php_uname, posix_getpwuid, setenv, main, apache_setenv, putenv, mail, link, mb_send_mail 
open_basedir = /var/www/html/
```
Restart Apache
```
service apache2 restart
```

B. Contoh menggunakan NGINX
```
nano /etc/php8.3/fpm/php.ini
```
Tambahkan di php.ini
```
disable_functions = show_source, system, passthru, exec, popen, proc_open,allow_url_fopen, symlink,exec,passthru,shell_exec,system,proc_open,popen,curl_multi_exec,parse_ini_file
open_basedir = /var/www/html/
```
Restart NGINX
```
service nginx restart
```

## Mengamankan phpMyAdmin
Edit Konfigurasi phpMyAdmin (Contoh menggunakan Apache)
```
nano /etc/phpmyadmin/apache.conf
```
Tambahkan di apache.conf
```
#Alias /phpMyAdmin /usr/share/phpMyAdmin <- Disable
Alias /secret_/usr/share/phpMyAdmin <- Enable
```
Restart Apache
```
service apache2 restart
```
