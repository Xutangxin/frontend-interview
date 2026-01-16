html 语义化标签  
header nav article section aside footer  
使用恰当语义的 html 标签，让页面具有良好的语义和结构  
好处：
开发者友好，便于维护
机器友好，适合搜索引擎爬虫爬取有效信息

html5 新特性  
表单（date,url,number,email 等）
音频视频标签

src 和 href 区别：  
src 指向外部资源所在位置，当浏览器解析到该元素时，会暂停其他资源的下载和处 理，直到将该资源加载、编译、执⾏完毕。  
href 指向网络资源所在位置，当浏览器识别到它他指向的 ⽂件时，就会并⾏下载资源，不会停⽌对当前⽂档的处理。

前端存储方式：  
cookie 携带在请求头中
sessionStorage 会话级别的存储方式， 页面关闭后会被清理
localStorage 永久性存储，除非手动删除

script async defer 区别  
async 下载完成后立即执行  
defer DOM 解析完成后，DOMContentLoaded 之前执行

canvas 和 svg 的区别  
canvas 依赖分辨率，缩放后模糊  
svg 不依赖分辨率，放大不模糊

xss 和 csrf  
XSS（跨站脚本攻击）：攻击者通过在网页中注入恶意脚本，窃取用户信息  
（转义输入输出的内容 ）  
CSRF（跨站请求伪造）：攻击者诱导用户在已登录的网站上执行非授权操作  
（csrf token + samesite cookie 属性）
