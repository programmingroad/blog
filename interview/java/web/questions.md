### session 和 cookie 有什么区别？
- session 在服务器端（文件，数据库，缓存），cookie 在客户端（浏览器）
- session通过session id来分辨客户端，而客户端一般使用cookie来存储session id

### 说一下 session 的工作原理？

### 如果客户端禁止 cookie 能实现 session 还能用吗？
一般默认情况下，在会话中，服务器存储 session 的 sessionid 是通过 cookie 存到浏览器里。

如果浏览器禁用了 cookie，浏览器请求服务器无法携带 sessionid，服务器无法识别请求中的用户身份，session失效。

但是可以通过其他方法在禁用 cookie 的情况下，可以继续使用session。

- 通过参数的形式携带session id

### 如何避免 sql 注入？
mybatis使用#代替$

### 什么是 XSS 攻击，如何避免？


### 什么是 CSRF 攻击，如何避免？
跨站请求伪造（英语：Cross-site request forgery），也被称为 one-click attack 或者 session riding，通常缩写为 CSRF 或者 XSRF， 是一种挟制用户在当前已登录的Web应用程序上执行非本意的操作的攻击方法。跟跨网站脚本（XSS）相比，XSS 利用的是用户对指定网站的信任，CSRF 利用的是网站对用户网页浏览器的信任。

- 避免措施
    - 检查Referer字段
    - 添加校验token