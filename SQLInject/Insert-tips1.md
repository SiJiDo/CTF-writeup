在sql注入中，如果存在insert的话，可以在字段中进行拼接

但是需要技巧，这里以在字段中添加数据库名的查询为例

```
'test1'+(select database())
```

![1558440861774](\img\Insert-tips1.png)

那么执行后会出现以下结果

![1558441007108](\img\Insert-tips2.png)

返回为0，但是如果利用如下技巧

```
'test1'+(select hex(database()))
```

![1558441115745](\img\Insert-tip3.png)

再进行16进制解码就能获取结果，如果太长可以使用substr来截取，这里就不再赘述

知识点来源于：RCTF2015 WEB update
