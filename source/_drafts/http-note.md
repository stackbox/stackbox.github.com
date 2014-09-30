title: http小记
date: 2014-08-31 00:10:31
tags: analysis
---



## 协议分析



除此之外，
curl显然支持这种情况，java的common-http库暂时不知道

但是rfc协议中对此好像没有明确的定义，参考


http://stackoverflow.com/questions/5216567/is-this-statement-correct-http-get-method-always-has-no-message-body


## Servlet参数解析

## $.ajax的注意事项

### 如何请求时带上header?

`$.ajax`中的 `beforeSend` 方法可以用来预先设置请求的header，示例如下

	$.ajax({
		url : 'http://www.flymeal.cn/test',
		type : 'GET',
		data : {a:1, b:2},
		beforeSend : function(request) {
			request.setRequestHeader("Authorization","BasicTest")
		},
		success : function(request) {
		}
	})

### 如何请求时request body?

**jQuery的GET请求无法附带request body，它还是把数据附加在请求url上**

1 . 比如你的data是一个字符串`"abcdeft"`，那么实际的请求就会变成下面这种情况了


	GET /test?abcdeft HTTP/1.1
	Host: www.flymeal.cn
	
2 . 如果data是一个js对象,那么实际请求的时候就会在url后面加上query string

	GET /test?a=1&b=2 HTTP/1.1
	Host: www.flymeal.cn

**POST请求则会把你的data附加到request body上**

1 . 如果你的data是一个js对象,比如 `{a:1, b:2}`,那么js会自动的把对象转成一个连接的查询字符串


	POST /test HTTP/1.1
	Host: www.flymeal.cn
	Connection: keep-alive
	Accept: */*
	X-Requested-With: XMLHttpRequest
	User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko)
	Authorization: BasicTest
	Referer: http://www.flymeal.cn/area/FLYJIAODA
	Accept-Encoding: gzip,deflate,sdch

	a=1&b=2
2 . 如果data是一个字符串，那么jQuery就会把这个字符串直接当成requestbody，比如data为 `JSON.stringify({a:1,b:2})`,则请求信息为


	POST /test HTTP/1.1
	Host: www.flymeal.cn
	Connection: keep-alive
	Accept: */*
	X-Requested-With: XMLHttpRequest
	User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko)
	Authorization: BasicTest
	Referer: http://www.flymeal.cn/area/FLYJIAODA
	Accept-Encoding: gzip,deflate,sdch

	{"a":1, "b":2}

同理，如果这个字符串是个xml，那么就是所谓的 **post一个xml到某个url** 了



注意，type为jsonp时用的是script而不是真正ajax

## 常见的cURL用法

`-H` 后面跟你的自定义Header