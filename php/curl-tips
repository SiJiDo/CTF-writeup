对于PHP的curl的各个参数的理解

curl_exec()可以发出curl请求



最简单的发出请求的写法

```
<?php
	$url = $_GET['url'];
	$ch = curl_init();
	curl_setopt($ch, CURLOPT_URL, $url);
	curl_exec($ch);
?>
```

对于`curl_setopt($ch, int $option, mixed $value )`是可以设置请求时的种种参数的

这里提下遇到的情况



1.`curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);`

默认值为**FALSE**。

 会使`curl_exec($ch);`执行后不会回显，而是返回成一个字符串，可以处理后用`echo`输出等

```
<?php
	$url = $_GET['url'];
	$ch = curl_init();
	curl_setopt($ch, CURLOPT_URL, $url);
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
	$data = curl_exec($ch);
	echo $data;
?>
```



2.`curl_setops($ch, CURLOPT_POSTFIELDS, $value)`

从 PHP 5.2.0 开始，使用 *@* 前缀传递文件时，`value` 必须是个数组。 从 PHP 5.5.0 开始, *@* 前缀已被废弃

加上@前缀时候，该值可以使用绝对路径读取文件内容，当然作为php触发ssrf漏洞的`curl`类的函数本身在没有防护下可以用`file://`读取文件内容，但是在一些协议被过滤的情况下，偶尔遇到这种情况还是一种思路



2.`curl_setopt($ch, CURLOPT_SAFE_UPLOAD, FALSE)`

PHP 5.5.0 中添加，默认值 **FALSE**。 PHP 5.6.0 改默认值为 **TRUE**。. PHP 7 删除了此选项

如果为**TRUE**可以禁用上面`CURLOPT_POSTFIELDS`特性使用@符号，如果为**FALSE**则可以使用



```
<?php
	$ch = curl_init("http://127.0.0.1:8000/api/ping");
	$value = array("url" => $_GET['url']);
	$ch = curl_init();
	curl_setopt($ch, CURLOPT_SAFE_UPLOAD, FALSE);  
	curl_setopt($ch, CURLOPT_POSTFIELDS, $value);
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
	$data = curl_exec($ch);
	echo $data;
?>
```

`127.0.0.1/index.php?url=@index.php`可以读取`index.php`信息,这里拿题目里面的·index.php·的内容作为参考



知识点来源 XCTF 4th-WHCTF-2017 WEB cat
