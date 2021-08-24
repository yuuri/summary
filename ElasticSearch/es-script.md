### 1. 目前elasticsearch 可以使用的几种script

1.painless
2.expression
3.mustache

几种语言的不同用法,例子为根据索引中已存在的一个字段构造一个不存在的字段
painless
```
GET tencent-web-access-backup/_search
{
  "script_fields": {
    "double_field": {
      "script": {
        "lang": "painless",
        "source": "return doc['log.offset'].value * params.get('pars');",
        "params": {"pars":2}
      }
    }
  }
}
```

expression
```
GET tencent-web-access-backup/_search
{
  "script_fields": {
    "double_field": {
      "script": {
        "lang": "expression",
        "source": "doc['log.offset'] * pars",
        "params": {"pars":2}
      }
    }
  }
}
```



