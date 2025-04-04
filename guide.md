#### HTML

# 让HTML和JSP页面不缓存从Web服务器上重新获取页面
## 问题描述
用户退出后，如果点击浏览器上的后退按钮，Web应用将不能正确保护受保护的页面——在Session销毁后（用户退出）受保护的JSP页重新在浏览器中显示出来。
然而，如果用户点击返回页面上的任何链接，Web应用将会跳转到登陆页面并提示Session has ended.Please log in.
## 解决方案
上述问题的根源在于大部分浏览器都有一个后退按钮。

##### `当点击后退按钮时，默认情况下浏览器不是从Web服务器上重新获取页面，而是从浏览器缓存中载入页面。`

基于Java的Web应用并未限制这一功能，在基于PHP、ASP和.NET的Web应用中也同样存在这一问题。
幸运的是，HTTP头信息“Expires”和“Cache-Control”为应用程序服务器提供了一个控制浏览器和代理服务器上缓存的机制。

##### HTTP头信息Expires告诉`代理服务器`它的缓存页面何时将过期。
##### HTTP1.1规范中新定义的头信息Cache-Control可以通知`浏览器`不缓存任何页面。

当点击后退按钮时，浏览器重新访问服务器已获取页面。

如下是使用Cache-Control的基本方法：

- ##### no-cache:强制缓存从服务器上获取新的页面
- ##### no-store: 在任何环境下缓存不保存任何页面

###### 保险起见，对html页面和jsp最好都加一些设置

对于HTML网页，加入：

    <!-- index.htm -->
    <meta HTTP-EQUIV="pragma" CONTENT="no-cache"> 
    <meta HTTP-EQUIV="Cache-Control" CONTENT="no-cache, must-revalidate"> 
    <meta HTTP-EQUIV="expires" CONTENT="0"> 

对于JSP页面，加入：

    <% 
    response.setHead("Cache-Control","no-store"); 
    response.setHeader("Pragrma","no-cache"); 
    response.setDateHeader("Expires",0); 
    %> 

就可以了。

## 补充
### Cache-Control: no-cache
这个很容易让人产生误解，使人误以为是响应不被缓存。`实际上Cache-Control: no-cache是会被缓存的，只不过每次在向客户端（浏览器）提供响应数据时，缓存都要向服务器评估缓存响应的有效性。`

### Pragma: no-cache
跟Cache-Control: no-cache相同，Pragma: no-cache兼容http 1.0 ，Cache-Control: no-cache是http 1.1提供的。因此，`Pragma: no-cache可以应用到http 1.0 和http 1.1,而Cache-Control: no-cache只能应用于http 1.1.`

> 内容来源：https://blog.csdn.net/weixin_43670802/article/details/105393738

* [回到首页](/)