
<p align="center"><strong><a href="https://hostvn.net">Hostvn.net - Tên miền, Web Hosting, Email, VPS &amp; Dịch vụ lưu trữ Website</a></strong></p>
<p align="center"> <img src="https://blog.hostvn.net/wp-content/uploads/2020/07/logo-big-2.png" /> </p>

#####################################################################################

## About Hostvn.net Docker PHP-FPM

Hostvn.net Docker PHP-FPM is developed based on the PHP Docker official, not only inherits the advantages of PHP Docker official but also helps to customize the configuration and add some extensions.

## Quick reference

- Maintained by: <a href="https://hostvn.net">Hostvn.net</a>
- Docker hub: https://hub.docker.com/r/hostvn/hostvn.net-php-fpm
- PHP Official: https://hub.docker.com/_/php
- Composer: https://getcomposer.org/

## Supported tags

- latest, 8.0.6, 7.4.19, 7.3.28

## PHP Extensions

- bcmath
- bz2
- calendar
- Core
- ctype
- curl
- date
- dom
- exif
- fileinfo
- filter
- ftp
- gd
- gettext
- hash
- iconv
- imagick (PHP 7)
- imap
- intl
- json
- ldap
- libxml
- mbstring
- memcached
- mongodb
- mysqli
- mysqlnd
- openssl
- pcre
- PDO
- pdo_mysql
- pdo_pgsql
- pdo_sqlite
- pgsql
- Phar
- posix
- readline
- redis
- Reflection
- session
- SimpleXML
- soap
- sockets
- sodium
- SPL
- sqlite3
- standard
- tokenizer
- xml
- xmlreader
- xmlrpc
- xmlwriter
- xsl
- json
- Zend OPcache
- zip
- zlib
- igbinary

## Custom config

- Opcache config: <b>/usr/local/etc/php/conf.d/docker-php-ext-opcache.ini</b>
- Opcache blacklist: <b>/usr/local/etc/php/conf.d/opcache-default.blacklist</b>
- Edit php parameters in: <b>/usr/local/etc/php/conf.d/00-hostvn-custom.ini</b>
- You can refer to the php configuration for the website in the file: <b>/usr/local/etc/php-fpm.d/pool.conf.example</b>

## Disable functions

Edit in <b>/usr/local/etc/php/conf.d/00-hostvn-custom.ini</b>

```html
exec,system,passthru,shell_exec,proc_close,proc_open,dl,popen,show_source,posix_kill,posix_mkfifo,posix_getpwuid,posix_setpgid,posix_setsid,posix_setuid,posix_setgid,posix_seteuid,posix_setegid,posix_uname
```

## Composer

Install two versions of composer.

- To use composer 2 run the command: <b>composer</b>
- To use composer 1 run the command: <b>composer1</b>

## Using:

```html
docker run --name php -h php --restart always -v /root/web:/var/www/html -d hostvn/hostvn.net-php-fpm
```

You can refer to how to use here: https://hub.docker.com/_/php
