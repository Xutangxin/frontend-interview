响应式原理  
Vue 响应式核心是数据劫持+依赖收集。  
Vue 2 用 Object.defineProperty 递归遍历对象每个属性，转为 getter/setter。数组通过重写 7 个方法实现监听。  
Vue 3 用 Proxy 代理整个对象，能监听增删改查所有操作，性能更好。
当数据被读取时，收集当前组件的渲染函数作为依赖；数据修改时，通知所有依赖重新执行，更新视图。

mvc 和 mvvm  
"MVC 是传统的分层架构，用户操作由 Controller 处理，然后更新 Model，最后 Controller 通知 View 重新渲染。需要手动更新视图，适合后端应用。
MVVM 是前端数据驱动架构，核心是数据双向绑定。ViewModel 作为中间层，通过响应式系统自动同步 View 和 Model。数据变化时视图自动更新，大大减少了 DOM 操作，适合复杂交互的前端应用

vue2 和 vue3 对比
响应式原理  
性能  
composition api  
hook  
teleport  
ts 支持

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
