# HTTP notes

## HTTP是什么

HTTP全称是Hypertext Transfer Protocol, 叫超文本转换协议。

## HTTP message

有两种HTTP message，分别是

- Request message
- Response message

一个HTTP message包含以下几部分。

- A start line. (Required)
- A set of headers. (？请核对清楚headers是optional还是required)
- A blank line. (Required)
- A body. (Optional)

例如以下的request message.
```
GET / HTTP/1.1
Host: localhost:1234
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.181 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
```

还有response message.
```
HTTP/1.1 200 Content-Type: text/plain
Date: Fri, 18 May 2018 14:20:58 GMT
Connection: keep-alive
Transfer-Encoding: chunked
```

Note: 以上的request message和response message是基于以下node.js的http server.

```js
const http = require('http');

const server = http.createServer();
server.on('request', (req, res) => {
	res.writeHead(200, 'Content-Type: text/plain');
	res.write('Welcome!');
	res.end();
});
server.listen(1234, () => console.log('The server is listening...'));
```

### Start line

对于一个request message, start line包含了3部分内容。

- HTTP method. 如`GET`.
- URL. 如`/`. (？此部分请核对清楚)
- HTTP version. 如`HTTP/1.1`.

对于一个response message, start line也包含了3部分内容。

- HTTP version.
- Status code. 如`200`
- Status message. 如上面的例子没有。

### Headers
### Body