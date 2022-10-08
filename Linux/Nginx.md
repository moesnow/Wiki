# Nginx

## Force https

```Nginx
if ($scheme = http) {
    return 301 https://$host$request_uri;
}
```

## Hide version

```Nginx
server_tokens  off;
```

```Tengine
# Tengine
server_info    off;
server_tag     off;
```

## Cache Control

```Nginx
location ~ .*\.(js|css|mp3|mp4|webm|woff2|ico|gif|jpg|jpeg|png|webp|bmp|swf|svg)$ {
    expires 7d;
}
```

## Autoindex

```Nginx
autoindex on;
autoindex_format html;
autoindex_exact_size off;
autoindex_localtime on;
charset utf-8,gbk;
```

## Enable SSL

```bash
openssl dhparam -out dhparam.pem 2048
```

```Nginx
ssl_certificate /path/to/.cer;
ssl_certificate_key /path/to/.key;

ssl_prefer_server_ciphers  on;
ssl_protocols TLSv1.2 TLSv1.3;
ssl_dhparam /path/to/dhparam.pem;
ssl_ciphers TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:TLS13-AES-128-CCM-8-SHA256:TLS13-AES-128-CCM-SHA256:EECDH+CHACHA20:EECDH+CHACHA20-draft:EECDH+ECDSA+AES128:EECDH+aRSA+AES128:RSA+AES128:EECDH+ECDSA+AES256:EECDH+aRSA+AES256:RSA+AES256:EECDH+ECDSA+3DES:EECDH+aRSA+3DES:RSA+3DES:!MD5;
```

## Enable PHP

### pathinfo.conf

```Nginx
fastcgi_split_path_info ^(.+?\.php)(/.*)$;
set $path_info $fastcgi_path_info;
fastcgi_param PATH_INFO       $path_info;
try_files $fastcgi_script_name =404;
```
### enable-php.conf

```Nginx
location ~ [^/]\.php(/|$)
{
    try_files $uri =404;
    fastcgi_pass  unix:/var/run/php/php.sock;
    fastcgi_index index.php;
    include fastcgi.conf;
}
```
### enable-php-pathinfo.conf

```Nginx
location ~ [^/]\.php(/|$)
{
    fastcgi_pass  unix:/var/run/php/php.sock;
    fastcgi_index index.php;
    include fastcgi.conf;
    include pathinfo.conf;
}
```

## Enable Authentication

```bash
# Debian & Ubuntu
apt install -y apache2-utils
# CentOS
yum install -y httpd-tools

htpasswd -c /path/to/.htpasswd user1
htpasswd /path/to/.htpasswd user2
```

```Nginx
location / {
    auth_basic "Authorized users only";
    auth_basic_user_file /path/to/.htpasswd;
}
```

## Disable direct access

### http

```Nginx
server{
    listen 80 default;
    server_name _;
    return 444;
}
```

### https

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt -subj '/CN=<SERVER-IP>'
```

```Nginx
server {
    listen 443 ssl default;
    server_name _;
    ssl_certificate         /path/to/certificate.crt;
    ssl_certificate_key     /path/to/privateKey.key;
    ssl_reject_handshake on; # Nginx 1.19.4
    return 444;
}
```

## Disable http methods

```Nginx
if ($request_method !~ ^(GET|HEAD|POST)$ )
{
    return 444;
}
```

## Reverse proxy

```Nginx
location / {
    proxy_redirect off;
    proxy_pass http://127.0.0.1:8080;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
```
