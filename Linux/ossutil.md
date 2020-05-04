# ossutil

> https://help.aliyun.com/document_detail/50452.html

1. `wget http://gosspublic.alicdn.com/ossutil/1.6.12/ossutil64 && chmod 755 ossutil64 && mv ossutil64 /usr/local/bin`

2. `vi ~/.ossutilconfig`

```vim
[Credentials]
language=CH
endpoint=oss-cn-shanghai.aliyuncs.com
accessKeyID=
accessKeySecret=
```

### Cache Control

`--meta=Cache-Control:max-age=86400`
