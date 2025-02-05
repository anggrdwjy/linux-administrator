## Melihat log Web Server
Apache2
```
cat /var/log/apache2/access.log
```
NGINX
```
cat /var/log/nginx/access.log
```
Monitor Log (Live)
```
tail -f ./access.log
```

## Mengamankan Server dari DOS (Denial of Service)
Tambahkan IPTABLES
```
iptables -I INPUT -p tcp --dport 80 -m connlimit --connlimit-above 20 --connlimit-mask 40 -j DROP
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
disable_functions = curl_multi_exec, popen, passthru, exec, popen, symlink, proc_open, shell_exec, show_source, allow_url_fopen, system, passthru, parse_ini_file, show_source, exec, proc_open, php_uname, posix_getpwuid, setenv, main, apache_setenv, putenv, mail, link, mb_send_mail,pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wifcontinued,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_get_handler,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,pcntl_async_signals,pcntl_unshare,phpinfo,putenv

open_basedir = /var/www/html
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
;disable_functions = curl_multi_exec, popen, passthru, exec, popen, symlink, proc_open, shell_exec, show_source, allow_url_fopen, system, passthru, parse_ini_file, show_source, exec, proc_open, php_uname, posix_getpwuid, setenv, main, apache_setenv, putenv, mail, link, mb_send_mail,pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wifcontinued,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_get_handler,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,pcntl_async_signals,pcntl_unshare,phpinfo,putenv

open_basedir = /var/www/html
```
Restart NGINX
```
service nginx restart
```
Catatan : Cara di atas tidak benar-benar aman karena masih bisa diremote dengan teknik tertentu. 

## Mengamankan phpMyAdmin
Edit Konfigurasi phpMyAdmin (Contoh menggunakan Apache)
```
nano /etc/phpmyadmin/apache.conf
```
Tambahkan di apache.conf
```
#Alias /phpMyAdmin /usr/share/phpMyAdmin <- Disable
Alias /hidden_/usr/share/phpMyAdmin <- Enable
```

Restart Apache
```
service apache2 restart
```
