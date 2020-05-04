# coscmd

> https://cloud.tencent.com/document/product/436/10976

1. `pip install coscmd`

2. `vi ~/.cos.conf`

```vim
[common]
secret_id =
secret_key =
bucket =
region = ap-shanghai
max_thread = 5
part_size = 1
schema = https
verify = md5
anonymous = False
```

### Cache Control

`-H "{'Cache-Control':'max-age=31536000'}"`
