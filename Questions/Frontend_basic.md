# Frontend Basic

### Q: Http v.s Https
```
https 的SSL 加密是在传输层实现的。
(1)http 和https 的基本概念
http: 超文本传输协议，是互联网上应用最为广泛的一种网络协议，是一个客户端和服
务器端请求和应答的标准（TCP），用于从WWW 服务器传输超文本到本地浏览器的传
输协议，它可以使浏览器更加高效，使网络传输减少。
https: 是以安全为目标的HTTP 通道，简单讲是HTTP 的安全版，即HTTP 下加入SSL
层，HTTPS 的安全基础是SSL，因此加密的详细内容就需要SSL。
https 协议的主要作用是：建立一个信息安全通道，来确保数组的传输，确保网站的真实
性。

(2)http 和https 的区别？
http 传输的数据都是未加密的，也就是明文的，网景公司设置了SSL 协议来对http 协议
传输的数据进行加密处理，简单来说https 协议是由http 和ssl 协议构建的可进行加密传
输和身份认证的网络协议，比http 协议的安全性更高。
主要的区别如下：
Https 协议需要ca 证书，费用较高。
http 是超文本传输协议，信息是明文传输，https 则是具有安全性的ssl 加密传输协议。
使用不同的链接方式，端口也不同，一般而言，http 协议的端口为80，https 的端口为
443
http 的连接很简单，是无状态的；HTTPS 协议是由SSL+HTTP 协议构建的可进行加密传
输、身份认证的网络协议，比http 协议安全。

(3)https 协议的工作原理
客户端在使用HTTPS 方式与Web 服务器通信时有以下几个步骤，如图所示。
客户使用https url 访问服务器，则要求web 服务器建立ssl 链接。
web 服务器接收到客户端的请求之后，会将网站的证书（证书中包含了公钥），返回或
者说传输给客户端。
客户端和web 服务器端开始协商SSL 链接的安全等级，也就是加密等级。
客户端浏览器通过双方协商一致的安全等级，建立会话密钥，然后通过网站的公钥来加
密会话密钥，并传送给网站。
web 服务器通过自己的私钥解密出会话密钥。
web 服务器通过会话密钥加密与客户端之间的通信。

(4)https 协议的优点
使用HTTPS 协议可认证用户和服务器，确保数据发送到正确的客户机和服务器；
HTTPS 协议是由SSL+HTTP 协议构建的可进行加密传输、身份认证的网络协议，要比
http 协议安全，可防止数据在传输过程中不被窃取、改变，确保数据的完整性。
HTTPS 是现行架构下最安全的解决方案，虽然不是绝对安全，但它大幅增加了中间人攻
击的成本。
谷歌曾在2014 年8 月份调整搜索引擎算法，并称“比起同等HTTP 网站，采用HTTPS
加密的网站在搜索结果中的排名将会更高”。

(5)https 协议的缺点
https 握手阶段比较费时，会使页面加载时间延长50%，增加10%~20%的耗电。
https 缓存不如http 高效，会增加数据开销。
SSL 证书也需要钱，功能越强大的证书费用越高。
SSL 证书需要绑定IP，不能再同一个ip 上绑定多个域名，ipv4 资源支持不了这种消耗。
```

### Q: BOM, DOM
```
DOM 指的是文档对象模型，它指的是把文档当做一个对象来对待，这个对象主要定义了处理网页内容的方法和接口。

BOM 指的是浏览器对象模型，它指的是把浏览器当做一个对象来对待，这个对象主要定义了与浏览器进行交互的方法和接口。
BOM的核心是 window，而 window 对象具有双重角色，它既是通过 js 访问浏览器窗口的一个接口，又是一个 Global（全局）
对象。这意味着在网页中定义的任何对象，变量和函数，都作为全局对象的一个属性或者方法存在。window 对象含有 locati
on 对象、navigator 对象、screen 对象、history对象等子对象，并且 DOM 的最根本的对象 document 对象也是 BOM 的 window 对
象的子对象。

(1)location 对象
location.href-- 返回或设置当前文档的URL
location.search -- 返回URL 中的查询字符串部分。例如http://www.dreamdu.com/dreamdu.php?id=5&name=dreamdu 返回包括(?)后面的内容?id=5&name=dreamdu
location.hash -- 返回URL#后面的内容，如果没有#，返回空
location.host -- 返回URL 中的域名部分，例如www.dreamdu.com
location.hostname -- 返回URL 中的主域名部分，例如dreamdu.com
location.pathname -- 返回URL 的域名后的部分。例如http://www.dreamdu.com/xhtml/ 返回/xhtml/
location.port -- 返回URL 中的端口部分。例如http://www.dreamdu.com:8080/xhtml/ 返回8080
location.protocol -- 返回URL 中的协议部分。例如http://www.dreamdu.com:8080/xhtml/ 返回(//)前面的内容http:
location.assign -- 设置当前文档的URL
location.replace() -- 设置当前文档的URL，并且在history 对象的地址列表中移除这个URL location.replace(url);
location.reload() -- 重载当前页面

(2)history 对象
history.go() -- 前进或后退指定的页面数history.go(num);
history.back() -- 后退一页
history.forward() -- 前进一页

(3)Navigator 对象
navigator.userAgent -- 返回用户代理头的字符串表示(就是包括浏览器版本信息等的字符串)
navigator.cookieEnabled -- 返回浏览器是否支持(启用)cookie

```

### Q: HTTP Status Code
```
100 Continue 继续。客户端应继续其请求
101 Switching Protocols 切换协议。服务器根据客户端的请求切换协议。只能切换到更高级的协议，例如，切换到HTTP 的新版本协议
200 OK 请求成功。一般用于GET 与POST 请求
201 Created 已创建。成功请求并创建了新的资源
202 Accepted 已接受。已经接受请求，但未处理完成
203 Non-Authoritative Information 非授权信息。请求成功。但返回的meta 信息不在原始的服务器，而是一个副本
204 No Content 无内容。服务器成功处理，但未返回内容。在未更新网页的情况下，可确保浏览器继续显示当前文档
205 Reset Content 重置内容。服务器处理成功，用户终端（例如：浏览器）应重置文档视图。可通过此返回码清除浏览器的表单域
206 Partial Content 部分内容。服务器成功处理了部分GET 请求
300 Multiple Choices 多种选择。请求的资源可包括多个位置，相应可返回一个资源特征与地址的列表用于用户终端（例如：浏览器）选择
301 Moved Permanently 永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI 代替
302 Found 临时移动。与301 类似。但资源只是临时被移动。客户端应继续使用原有URI
303 See Other 查看其它地址。与301 类似。使用GET 和POST 请求查看
304 Not Modified 未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源
305 Use Proxy 使用代理。所请求的资源必须通过代理访问
306 Unused 已经被废弃的HTTP 状态码
307 Temporary Redirect 临时重定向。与302 类似。使用GET 请求重定向
400 Bad Request 客户端请求的语法错误，服务器无法理解
401 Unauthorized 请求要求用户的身份认证
402 Payment Required 保留，将来使用
403 Forbidden 服务器理解请求客户端的请求，但是拒绝执行此请求
404 Not Found 服务器无法根据客户端的请求找到资源（网页）。通过此代码，网站设计人员可设置"您所请求的资源无法找到"的个性页面
405 Method Not Allowed 客户端请求中的方法被禁止
406 Not Acceptable 服务器无法根据客户端请求的内容特性完成请求
407 Proxy Authentication Required 请求要求代理的身份认证，与401 类似，但请求者应当使用代理进行授权
408 Request Time-out 服务器等待客户端发送的请求时间过长，超时
409 Conflict 服务器完成客户端的PUT 请求是可能返回此代码，服务器处理请求时发生了冲突
410 Gone 客户端请求的资源已经不存在。410 不同于404，如果资源以前有现在被永久删除了可使用410 代码，网站设计人员可通过301 代码指定资源的新位置
411 Length Required 服务器无法处理客户端发送的不带Content-Length 的请求信息
412 Precondition Failed 客户端请求信息的先决条件错误
413 Request Entity Too Large 由于请求的实体过大，服务器无法处理，因此拒绝请求。为防止客户端的连续请求，服务器可能会关闭连接。如果只是服务器暂时无法处理，则会包含一个Retry-After 的响应信息
414 Request-URI Too Large 请求的URI 过长（URI 通常为网址），服务器无法处理
415 Unsupported Media Type 服务器无法处理请求附带的媒体格式
416 Requested range not satisfiable 客户端请求的范围无效
417 Expectation Failed 服务器无法满足Expect 的请求头信息
500 Internal Server Error 服务器内部错误，无法完成请求
501 Not Implemented 服务器不支持请求的功能，无法完成请求
502 Bad Gateway 作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应
```

### Q: Why fetch request will send twice?
```
fetch 发送post 请求的时候，总是发送2 次，第一次状态码是204，第二次才成功？
原因很简单，因为你用fetch 的post 请求的时候，导致fetch 第一次发送了一个Options
请求，询问服务器是否支持修改的请求头，如果服务器支持，则在第二次中发送真正的
请求
```

### Q: Cookie, sessionStorage, LocalStorage
```
共同点：都是保存在浏览器端，并且是同源的

Cookie：cookie 数据始终在同源的http 请求中携带（即使不需要），即cookie 在浏览器
和服务器间来回传递。而sessionStorage 和localStorage 不会自动把数据发给服务器，仅
在本地保存。cookie 数据还有路径（path）的概念，可以限制cookie 只属于某个路径下,
存储的大小很小只有4K 左右。（key：可以在浏览器和服务器端来回传递，存储容量
小，只有大约4K 左右）

sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持，localStorage：
始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie 只在设置的cookie
过期时间之前一直有效，即使窗口或浏览器关闭。（key：本身就是一个回话过程，关
闭浏览器后消失，session 为一个回话，当页面不同即使是同一页面打开两次，也被视为
同一次回话）

localStorage：localStorage 在所有同源窗口中都是共享的；cookie 也是在所有同源窗口中
都是共享的。（key：同源窗口都会共享，并且不会失效，不管窗口或者浏览器关闭与
否都会始终生效）

补充说明一下cookie 的作用：
保存用户登录状态。例如将用户id 存储于一个cookie 内，这样当用户下次访问该页面
时就不需要重新登录了，现在很多论坛和社区都提供这样的功能。cookie 还可以设置
过期时间，当超过时间期限后，cookie 就会自动消失。因此，系统往往可以提示用户保
持登录状态的时间：常见选项有一个月、三个月、一年等。

跟踪用户行为。例如一个天气预报网站，能够根据用户选择的地区显示当地的天气情况。
如果每次都需要选择所在地是烦琐的，当利用了cookie 后就会显得很人性化了，系统能
够记住上一次访问的地区，当下次再打开该页面时，它就会自动显示上次用户所在地区
的天气情况。因为一切都是在后台完成，所以这样的页面就像为某个用户所定制的一
样，使用起来非常方便定制页面。如果网站提供了换肤或更换布局的功能，那么可以使
用cookie 来记录用户的选项，例如：背景色、分辨率等。当用户下次访问时，仍然可以
保存上一次访问的界面风格。
```

### Q: Web Worker
```
在HTML 页面中，如果在执行脚本时，页面的状态是不可相应的，直到脚本执行完成后，
页面才变成可相应。web worker 是运行在后台的js，独立于其他脚本，不会影响页面你
的性能。并且通过postMessage 将结果回传到主线程。这样在进行复杂操作的时候，就
不会阻塞主线程了。

如何创建web worker：
检测浏览器对于web worker 的支持性
创建web worker 文件（js，回传函数等）
创建web worker 对象
```

### Q: iframe
```
定义：iframe 元素会创建包含另一个文档的内联框架
提示：可以将提示文字放在<iframe></iframe>之间，来提示某些不支持iframe 的浏览器

缺点：
会阻塞主页面的onload 事件
搜索引擎无法解读这种页面，不利于SEO
iframe 和主页面共享连接池，而浏览器对相同区域有限制所以会影响性能。
```