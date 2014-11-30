##WSGI基础知识
> 翻译自`Basics of WSGI`[http://agiliq.com/blog/2013/07/basics-wsgi/](http://agiliq.com/blog/2013/07/basics-wsgi/)

在这篇文章里，我们将会写一个web app，这个app它会服务一些url。我们将不会使用任何Python框架来写它。我们只是去说明一下这些机制的背后原理。

在开始写这个web app之前，我们先来澄清几个下文将要用到的术语。


- **Web服务器(Web Server)**: 当我们说Web 服务器时，我们指的是软件，而不是那些存储你代码的硬件机器。这个服务器会接收从客户端(Web浏览器)发送过来的请求并返回一个响应(response)。Web服务器本身并不创建响应，它只负责返回响应。所以，Web服务器就需要同Web应用程序交流，因为Web应用程序它能产生响应。


- **Web应用程序(Web Application)**:Web服务器从它这里拿到响应。Web Application的职责就是根据url来创建响应并将响应传回给Web服务器。然后Web服务器就只是返回这个响应到客户端而已。


- **WSGI**: WSGI是一个接口，它只是一份规范或者说是一系列的规则。WSIG不是一个软件。

WSGI会引起人们的注意是因为Web服务器需要跟Web应用程序通信。WSGI规定了Web应用程序和Web服务器双方必须实现的规则，以便让它们之间能够互相交互。这么说吧，一个符合WSGI规范的服务器就可以跟一个符合WSGI规范的Web应用程序通信。

在WSGI架构里，WSGI应用程序必须是一个可调用者(callable)，并且这个可调用者(callable)必须被传递给Web服务器，这样不管什么时候，只要Web服务器接收到客户端的一个请求，它就能随时调用Web应用程序。

想要了解更多关于为什么WSGI会得以出现的原因，请参照 [WSGI的维基百科](http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface)。

现在开始写我们的Web应用程序。你暂时只需要全部拷贝下面的代码即可，我们稍后会对每一行代码做详细解释以便清楚地知道它们都做了什么。
```python
#web_application.py
from wsgiref.simple_server import make_server

def application(environ, start_response):
    path = environ.get('PATH_INFO')
    if path == '/':
        response_body = "Index"
    else:
        response_body = "Hello"
    status = "200 OK"
    response_headers = [("Content-Length", str(len(response_body)))]
    start_response(status, response_headers)
    return [response_body]

httpd = make_server(
    '127.0.0.1', 8051, application)

httpd.serve_forever()
```
这个脚本可以通过运行命令`python web_application.py`来执行，接着你可以在浏览器中访问链接`http://127.0.0.1:8051/`和`http://127.0.0.1:8051/abcd`。你将看到第一个页面会返回Index，而第二个页面返回Hello。

现在，我们来逐句分析下代码。

- Python提供了一个方法叫做`make_server`。我们可以用它来创建一个遵循WSGI规范的基于Python的Web服务器。
- 我们创建了一个`callable`叫做`application`。你可以认为这个`callable`就是上文所说的Web应用程序。
- `make_server()`方法创建了一个遵循WSGI规范的web服务器。这里的`httpd`就是Web服务器。
- `make_server()`的前两个参数指定了主机(host)以及Web服务器监听请求的端口(port)。
- `make_server()`的第三个参数是Web应用程序，Web服务器将利用这个参数来获取响应。
- 代码的最后一行通过`serve_forever`来启动Web服务器。 

不管什么时候，只要有请求进来，运行在8051端口的Web服务器就会去调用Web应用程序，在我们这个例子里，Web应用程序就是callable `application`.

下面是关于Web应用程序代码的细节。

- 为了能和WSGI的Web服务器交互，Web应用程序同样也必须遵循WSGI规范。
- 服务器调用它时需要两个参数。所以，它必须接收两个参数，这是Web应用程序遵循WSGI规范的第一个条件。
- 传给它的第一个参数是包含了许多关于请求(request)信息的一个变量。在我们这个例子里，我们用它来读取请求的路径。
- 传给它的第二个参数是一个`callable`。应用程序必须利用这个`callable`来通知服务器关于响应的状态以及设定各种报头(headers)。这是Web应用程序遵循WSGI规范的第二个条件。
- 我们的应用程序满足了遵循WSGI规范所要求的两个条件。
- 最后，应用程序返回一个响应给WSGI服务器。
- 然后，服务器最终会转发这个响应给客户端。


###编辑:
我之前在**application**的代码里忽略了一件事，`defnull`童鞋在reddit上指出了我的错误。

**application**的最后一行不能返回**`response_body`**，正确的情况是它应该返回**`[response_body]`**。原因是：

- WSGI服务器期望从应用程序返回一个`iterable`然后它会将这个`iterable`的每一个元素以一种无缓冲的方式发送给客户端。
- 如果我们坚持返回`response_body`，那么`response_body`是一个string同时也是一个`iterable`，这样的话我们的代码确实还能正常工作不会报错。但是同时也使得`response_body`中的内容将会被一个字符一个字符地传递。
- 然而，如果我们返回的是`[response_body]`, 在这里，这`个iterable`是一个list, 这个list只有唯一一个元素即`response_body`字符串。这样，在我们这个例子里，整个`response_body`就只需要被传递一次。
- 这就是为什么我们应该返回`[response_body]`而不是`response_body`。上面的代码我已经改过来了。

你应该读读这篇[WSGI](http://webpython.codepoint.net/wsgi_tutorial)来了解更多关于WSGI。

### 译者注
- 更新时间：`2014-11-28`
- 本人翻译的初衷是为了自身学习和记录，翻译不好的地方，还望读者见谅.
