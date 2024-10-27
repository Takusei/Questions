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

### Q: Doctype?
```
Tell browser use which method to read the document, there are 2 types:
stands-mode, quirks-mode
```

### Q: XSS attack?
```
Cross Site Scripting
XSS 攻击指的是跨站脚本攻击，是一种代码注入攻击。攻击者通过在网站注入恶意脚本，使之在用户的浏览器上运行，从而盗取用户的信息如 cookie 等。

XSS 的本质是因为网站没有对恶意代码进行过滤，与正常的代码混合在一起了，浏览器没有办法分辨哪些脚本是可信的，从而导致了恶意代码的执行。

XSS 一般分为存储型、反射型和 DOM 型。

Stored XSS 
存储型指的是恶意代码提交到了网站的数据库中，当用户请求数据的时候，服务器将其拼接为 HTML 后返回给了用户，从而导致了恶意代码的执行。

Reflected XSS
反射型指的是攻击者构建了特殊的 URL，当服务器接收到请求后，从 URL 中获取数据，拼接到 HTML 后返回，从而导致了恶意代码的执行。

DOM Based XSS
DOM 型指的是攻击者构建了特殊的 URL，用户打开网站后，js 脚本从 URL 中获取数据，从而导致了恶意代码的执行。

XSS 攻击的预防可以从两个方面入手，一个是恶意代码提交的时候，一个是浏览器执行恶意代码的时候。

对于第一个方面，如果我们对存入数据库的数据都进行的转义处理，但是一个数据可能在多个地方使用，有的地方可能不需要转义，由于我们没有办法判断数据最后的使用场景，所以直接在输入端进行恶意代码的处理，其实是不太可靠的。

因此我们可以从浏览器的执行来进行预防，一种是使用纯前端的方式，不用服务器端拼接后返回。另一种是对需要插入到 HTML 中的代码做好充分的转义。对于 DOM 型的攻击，主要是前端脚本的不可靠而造成的，我们对于数据获取渲染和字符串拼接的时候应该对可能出现的恶意代码情况进行判断。

还有一些方式，比如使用 CSP ，CSP 的本质是建立一个白名单，告诉浏览器哪些外部资源可以加载和执行，从而防止恶意代码的注入攻击。

还可以对一些敏感信息进行保护，比如 cookie 使用 http-only ，使得脚本无法获取。也可以使用验证码，避免脚本伪装成用户执行一些操作。

```
### Q: CSP?
```
Content-Security-Policy
CSP 指的是内容安全策略，它的本质是建立一个白名单，告诉浏览器哪些外部资源可以加载和执行。
我们只需要配置规则，如何拦截由浏览器自己来实现。

通常有两种方式来开启 CSP，一种是设置 HTTP 首部中的 Content-Security-Policy，
一种是设置 meta 标签的方式 <metahttp-equiv="Content-Security-Policy">
```


### Q: CSRF attack?
```
Cross-site request forgery
是一种挟制用户在当前已登录的Web应用程序上执行非本意的操作的攻击方法。跟跨网站脚本（XSS）相比，XSS利用的是用户对指定网站的信任，CSRF利用的是网站对用户网页浏览器的信任

CSRF 攻击指的是跨站请求伪造攻击，攻击者诱导用户进入一个第三方网站，然后该网站向被攻击网站发送跨站请求。
如果用户在被攻击网站中保存了登录状态，那么攻击者就可以利用这个登录状态，绕过后台的用户验证，冒充用户向服务器执行一些操作。

CSRF 攻击的本质是利用了 cookie 会在同源请求中携带发送给服务器的特点，以此来实现用户的冒充。

一般的 CSRF 攻击类型有三种：

第一种是 GET 类型的 CSRF 攻击，比如在网站中的一个 img 标签里构建一个请求，当用户打开这个网站的时候就会自动发起提
交。

第二种是 POST 类型的 CSRF 攻击，比如说构建一个表单，然后隐藏它，当用户进入页面时，自动提交这个表单。

第三种是链接类型的 CSRF 攻击，比如说在 a 标签的 href 属性里构建一个请求，然后诱导用户去点击。

CSRF 可以用下面几种方法来防护：

第一种是同源检测的方法，服务器根据 http 请求头中 origin 或者 referer 信息来判断请求是否为允许访问的站点，从而对请求进行过滤。当 origin 或者 referer 信息都不存在的时候，直接阻止。这种方式的缺点是有些情况下 referer 可以被伪造。还有就是我们这种方法同时把搜索引擎的链接也给屏蔽了，所以一般网站会允许搜索引擎的页面请求，但是相应的页面请求这种请求方式也可能被攻击者给利用。

第二种方法是使用 CSRF Token 来进行验证，服务器向用户返回一个随机数 Token ，当网站再次发起请求时，在请求参数中加入服务器端返回的 token ，然后服务器对这个 token 进行验证。这种方法解决了使用 cookie 单一验证方式时，可能会被冒用的问题，但是这种方法存在一个缺点就是，我们需要给网站中的所有请求都添加上这个 token，操作比较繁琐。还有一个问题是一般不会只有一台网站服务器，如果我们的请求经过负载平衡转移到了其他的服务器，但是这个服务器的 session 中没有保留这个 token 的话，就没有办法验证了。这种情况我们可以通过改变 token 的构建方式来解决。

第三种方式使用双重 Cookie 验证的办法，服务器在用户访问网站页面时，向请求域名注入一个Cookie，内容为随机字符串，然后当用户再次向服务器发送请求的时候，从 cookie 中取出这个字符串，添加到 URL 参数中，然后服务器通过对 cookie 中的数据和参数中的数据进行比较，来进行验证。使用这种方式是利用了攻击者只能利用 cookie，但是不能访问获取 cookie 的特点。并且这种方法比 CSRF Token 的方法更加方便，并且不涉及到分布式访问的问题。这种方法的缺点是如果网站存在 XSS 漏洞的，那么这种方式会失效。同时这种方式不能做到子域名的隔离。

第四种方式是使用在设置 cookie 属性的时候设置 Samesite ，限制 cookie 不能作为被第三方使用，从而可以避免被攻击者利用。Samesite 一共有两种模式，一种是严格模式，在严格模式下 cookie 在任何情况下都不可能作为第三方 Cookie 使用，在宽松模式下，cookie 可以被请求是 GET 请求，且会发生页面跳转的请求所使用。
```

### Q: Samesite cookie?
```
Samesite Cookie 表示同站 cookie，避免 cookie 被第三方所利用。

将 Samesite 设为 strict ，这种称为严格模式，表示这个 cookie 在任何情况下都不可能作为第三方 cookie。

将 Samesite 设为 Lax ，这种模式称为宽松模式，如果这个请求是个 GET 请求
，并且这个请求改变了当前页面或者打开了新的页面，那么这个 cookie 可以作为第三方 cookie，其余情况下都不能作为第三方 cookie。

使用这种方法的缺点是，因为它不支持子域，所以子域没有办法与主域共享登录信息，每次转入子域的网站，都回重新登录。
还有一个问题就是它的兼容性不够好。

```

### Q. 强缓存 协商缓存
```
强缓存 从缓存取  200（from cache） 直接从缓存取
协商缓存 从缓存取 304（not modified） 通过服务器来告知缓存是否可用

强缓存相关字段有expires，cache-control。如果cache-control 与expires 同时存在的话，
cache-control 的优先级高于expires。

协商缓存相关字段有Last-Modified/If-Modified-Since，Etag/If-None-Match
```


### Q. GET vs. POST
```
get 参数通过url 传递，post 放在request body 中。

get 请求在url 中传递的参数是有长度限制的，而post 没有。

get 比post 更不安全，因为参数直接暴露在url 中，所以不能用来传递敏感信息。

get 请求只能进行url 编码，而post 支持多种编码方式

get 请求会浏览器主动cache，而post 支持多种编码方式。

get 请求参数会被完整保留在浏览历史记录里，而post 中的参数不会被保留。

GET 和POST 本质上就是TCP 链接，并无差别。但是由于HTTP 的规定和浏览器/服务器
的限制，导致他们在应用过程中体现出一些不同。

GET 产生一个TCP 数据包；POST 产生两个TCP 数据包。
对于GET 方式的请求，浏览器会把http header 和data 一并发送出去，服务器响应200
（返回数据）；
而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服
务器响应200 ok（返回数据）

```

### Q. HTTP methods?
```
GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE, CONNECT
```

### Q. What will happen when you input url in the browser?
```
1. Find DNS
 - can from browser cache, system cache, router cache and etc.

2. Go to the ip to get content

3. Use return html to build DOM, CSSOM

4. Show to user

DNS 解析
TCP 连接
发送HTTP 请求
服务器处理请求并返回HTTP 报文
浏览器解析渲染页面
连接结束
```

### Q. web 性能优化
```
降低请求量：合并资源，减少HTTP 请求数，minify / gzip 压缩，webP，lazyLoad。

加快请求速度：预解析DNS，减少域名数，并行加载，CDN 分发。

缓存：HTTP 协议缓存请求，离线缓存manifest，离线数据缓存localStorage。

渲染：JS/CSS 优化，加载顺序，服务端渲染，pipeline。
```