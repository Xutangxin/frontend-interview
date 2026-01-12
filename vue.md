响应式原理  
Vue 2.0 的响应式原理主要依赖于 Object.defineProperty，它只能对属性进行监听，如果要对对象进行监听，需要递归遍历对象的所有属性。
Vue 3.0 的响应式原理主要依赖于 Proxy，它可以直接监听对象，不需要递归遍历对象的所有属性。

mvc 和 mvvm  
"MVC 是传统的分层架构，用户操作由 Controller 处理，然后更新 Model，最后 Controller 通知 View 重新渲染。需要手动更新视图，适合后端应用。
MVVM 是前端数据驱动架构，核心是数据双向绑定。ViewModel 作为中间层，通过响应式系统自动同步 View 和 Model。数据变化时视图自动更新，大大减少了 DOM 操作，适合复杂交互的前端应用

vue2 和 vue3 对比

组件通信

hash 模式 和 history 模式
hash 模式是通过 hash 值来实现路由跳转，history 模式是通过 HTML5 的 history 接口来实现路由跳转。
hash 模式的 URL 中包含 #，history 模式的 URL 中不包含 #。
hash 模式兼容性好，seo 效果较差，history 模式需要服务端支持,seo 效果较好。  
history 模式需要后端配置，是因为浏览器会把 SPA 的路由当作真实文件路径去请求服务器，比如用户访问 /dashboard，浏览器会直接向服务器请求这个路径，但 SPA 实际上只有一个 index.html，所以会返回 404。解决方案是：让服务器将所有前端路由重定向到 index.html，让 Vue Router 接管路由解析。

虚拟 dom 和 diff 算法

v-if 和 v-show 区别

computed 和 watch 区别

vue3 相关
