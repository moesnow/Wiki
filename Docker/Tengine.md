# Tengine

> http://tengine.taobao.org

### Dockerfile
```Dockerfile
FROM alpine:3.11

ENV TENGINE_VERSION 2.3.2

# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
#     && apk add tzdata && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

RUN addgroup -g 101 -S nginx && adduser -S -D -H -u 101 -h /var/cache/nginx -s /sbin/nologin -G nginx -g nginx nginx \
    && apk add --no-cache gcc libc-dev make openssl-dev pcre-dev zlib-dev linux-headers \
    && cd /tmp && wget https://tengine.taobao.org/download/tengine-${TENGINE_VERSION}.tar.gz \
    && tar zxvf tengine-${TENGINE_VERSION}.tar.gz && cd tengine-${TENGINE_VERSION} \

#   && sed -i 's|\\x85\\xde\\x5a\\xa6\\x35\\x45|\\x85\\xcc\\x74\\x9e\\xc3\\x7f|g' src/http/v2/ngx_http_v2_filter_module.c \

    && ./configure --prefix=/etc/nginx --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --user=nginx --group=nginx --with-compat --with-file-aio --with-threads --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module --with-cc-opt='-Os -fomit-frame-pointer' --with-ld-opt=-Wl,--as-needed \
    && make install \
    && apk del gcc libc-dev make openssl-dev zlib-dev linux-headers vim unzip \
    && rm -rf /var/cache/apk/* \
    && rm -rf /tmp/* \
    && ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
```

### Build

`docker build -t tengine:2.3.2-alpine .`

### Run

`docker run --name tengine -d -p 80:80 -p 443:443 -v /usr/local/etc/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v /usr/local/etc/nginx/conf.d:/etc/nginx/conf.d:ro -v /usr/local/etc/nginx/acme.sh:/etc/nginx/acme.sh:ro tengine:2.3.2-alpine`
