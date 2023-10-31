html语义化：
header nav article section aside footer
使用恰当语义的html标签，让页面具有良好的语义和结构
好处：
开发者友好，便于维护
机器友好，适合搜索引擎爬虫爬取有效信息

html5新特性
表单（date,url,number,email等）
音频视频标签

常用的meta标签
charset 用于描述文档编码格式
viewport 移动端控制视口大小和比例

src和href区别：
src指向外部资源所在位置，当浏览器解析到该元素时，会暂停其他资源的下载和处 理，直到将该资源加载、编译、执⾏完毕。
href指向网络资源所在位置，当浏览器识别到它他指向的 ⽂件时，就会并⾏下载资源，不会停⽌对当前⽂档的处理。

前端存储方式：
cookie 携带在请求头中
sessionStorage 会话级别的存储方式， 页面关闭后会被清理
localStorage 永久性存储，除非手动删除

css选择器优先级
内联样式>id选择器>类选择器=伪类选择器>标签选择器

css隐藏页面元素
display:none（设置none后不再占据空间）
opacity:0（不透明度设置为0）
visible:hidden（设置hidden后仍然占据空间，只是不可见而已）
overflow:hidden

em，rem，px区别
px是绝对单位，像素
em是相对单位，相对于父元素字体大小来算
rem是相对单位，相对于html字体大小来计算

块级元素水平垂直居中
margin:0, auto
flex布局（justify-content:center; align-items:center）
定位+margin（1.子绝父相 2.子元素各方向偏移大小设置为0 3.子元素添加margin：auto）
使用定位（子绝父相）+ transform:translate(-50%,-50%)，在此之前需加上top:50%;left:50%;

css有几种定位
static静态定位 元素默认的状态 使用较少
absoulate 相对于最近的带有定位的父元素
relative 相对定位 相对于自己原来的位置
fixed 固定定位 相对于屏幕视口位置来指定元素位置
sticky 粘性定位 相当于static+fixed 主要用在scroll事件的监听上；比如当子元素滑动到距离父元素一定距离时（满足sticky定位的距离），此时sticky相当于fixed定位，可以实现固定效果
 
什么是z-index
z-index用来控制重叠元素的垂直叠加顺序，只对加了定位的元素有效

清除浮动方法
空标签法（结尾处加空div标签 clear:both ）
父盒子使用overflow（hidden/auto）
伪元素法（父盒子添加伪元素）

对雪碧图的理解
将小图标合并在一起形成一张图片
优点：
减少请求次数，减小服务器压力
提前加载资源
缺点：
维护成本高
现在使用较少，一般使用字体图标

媒体查询
配合web网页根据不同设备尺寸来做出相应的尺寸适配（响应适配）
语法：
<style>
@media (max-width:200px){
    css代码。。。。。。
}
</style>

对盒模型的理解
margin border padding content

对BFC的理解
bfc 块级格式上下文，是一块独立的区域，其内部元素和外部元素相互隔离，互不影响
触发：
根元素，即html元素会触发bfc
position: fixed/absolute
float 不为none
overflow不为visible
display的值为inline-block、table-cell、table-caption
作用：
防止margin重叠
两栏布局
防止元素塌陷
清除浮动

伪类和伪元素
伪类：添加在选择器中，在特定条件下显示某种元素或改变元素状态
伪元素：可当作html元素使用，创建的为元素在dom树中不可见

对flex的理解
开发人员只是声明布局行为，浏览器来完成实际布局
适用场景：不定宽度，分布对齐等

line-height继承的三种情况	
具体像素值 例如30px 正常继承，子元素行高是父元素的行高
倍数 例如1.5 正常继承,子元素行高是自身字体大小*1.5
百分比 例如200% 子元素行高为父元素字体大小*200%

哪些属性是继承属性
常见的可继承属性：字体相关，颜色，元素可见性

支持跨域的html标签（img link script）
<script>标签和<img>标签的src属性支持跨域,浏览器对其没有限制,发送的请求都是get请求
<link>标签也支持跨域

Web Worker 和WebSocket
Web Worker：
web worker是运行在后台的js，独立于其他脚本，不会影响页面的性能
web worker可以实现创建多线程，当主线程运行时，web worker在后台运行，两者互不干扰，web worker完成计算任务后，将结果返回给主线程
web worker无法访问window和document对象
web worker和异步区别：web worker是真正的多线程，而异步不是真正的多线程

WebSocket：
客户端和服务端之间的建立在单个tcp连接上的全双工通信协议
特点：
客户端和服务端之间只要进行一次tcp握手，就可以建立持久性的连接，并实现双向数据传输
相比于轮询，使用websocket，客户端不用频繁的向服务端发送请求，有利于节省服务器和带宽资源
建立websocket连接后，使用send方法向服务端发送数据，使用onmessage事件获取服务端返回的数据