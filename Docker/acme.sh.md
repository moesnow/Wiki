# acme.sh

> https://github.com/acmesh-official/acme.sh

### Run

`docker run -itd  \
  -v "/usr/local/etc/nginx/acme.sh":/acme.sh  \
  -e SAVED_Ali_Key='' \
  -e SAVED_Ali_Secret='' \
  --net=host \
  --name=acme.sh \
  neilpang/acme.sh daemon`

```bash
docker exec -it acme.sh ash
acme.sh --issue -d your.domain -d '*.your.domain' --dns dns_ali
```
