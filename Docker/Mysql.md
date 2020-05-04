# Mysql

### Run

`docker run --name mysql -d -p 3306:3306 -v /usr/local/etc/mysql/conf.d:/etc/mysql/conf.d:ro -v /var/lib/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password mysql:5.7.29`

### conf.d/docker.cnf

```vim
[mysqld]
skip-host-cache
skip-name-resolve

ngram_token_size=2
```
