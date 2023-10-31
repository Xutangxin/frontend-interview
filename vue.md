
浏览器渲染过程：
浏览器获取到 HTML 文档并解析 DOM 树
解析 CSS 构建层叠样式表模型CSSOM(CSS Object Model)
将 DOM Tree 和 CSSOM 合并成一个 Render Tree
有了Render Tree，浏览器便能获取到每个节点的 CSS 定义和从属关系，从而可以计算出每个节点的现实位置
通过上一步的计算规则进行绘制页面

为什么需要虚拟dom:
用原生 js 或 jquery 去操作 DOM 时，浏览器会从构建 DOM 树到绘制全部执行一遍，会导致性能的浪费，操作频繁的话还可能会导致页面卡顿

虚拟dom原理：
用javascript对象模拟DOM树并且渲染DOM树；
通过 diff算法 比较新旧DOM树，得到差异的对象；
将差异的对象应用到渲染的DOM树中。

真实dom和虚拟dom对比：
真实dom：
<div id="app">
    哈哈
    <p>123</p>
</div>
虚拟dom：（一个js对象）
var vNode = {
    tag: 'div',
    props: {id: 'app'},
    children: [
        {
            tag: 'p',
            props: {},
            children: [],
            context: '123'
        }
    ],
    context: '哈哈'
}


diff算法
遍历老虚拟dom
遍历新虚拟dom
重新排序
对于新老虚拟dom的比较：
只比较同一层级，不跨级比较
标签名不同，直接删除，不继续进行深度比较
标签名和key值相同，认为是相同节点，不继续进行深度比较

对mvvm的理解
m：Model层，对应数据层的域模型，主要做域模型的同步
v：View层，作为视图模板存在，定义结构，数据，展示ViewModel层的数据和状态
vm：ViewModel层，中间层，暴露数据，处理view层的具体业务逻辑；监听绑定属性，当ViewModel层数据变化时，及时更新到view层
mvvm模型的优点：
分离视图和模型，提高视图或逻辑的重用性
自动更新dom
缺点：
较难调试
花费更多的内存
维护成本较高

vue的生命周期
beforeCreate 实例创建前
created 实例已创建
beforeMount 实例挂载前
mounted 实例已挂载
beforeUpdate 组件数据更新前
updated 组件数据已更新
activited keep-alive组件激活时
deadActivited keep-alive组件销毁时
beforeDestory 组件销毁前
destoryed 组件已销毁

异步请求在哪个生命周期调用
created和mounted

组件之间如何通信
父子组件：
父组件传递信息给子组件：props
子组件传递信息给父组件：$emit + v-on
兄弟组件之间传递信息：
eventBus 事件巴士
使用全局数据管理库vuex

computed和watch区别
computed：用于计算；有缓存；
watch：数据变化时执行，无缓存

vue如何实现双向绑定的
数据劫持+发布订阅的方式实现数据双向绑定：
通过劫持对象的访问器，在属性变化时可以获取变化，然后根据变化进行后续响应

vue中的key有什么用
key是vnode中唯一标记的id，通过key，diff操作可以更准确，更快速，不建议使用index作为key

v-show和v-if区别
对于不显示的元素，v-if直接不会渲染到dom树中，而v-show会渲染，只是把display设置为了none

v-html特点
通过v-html渲染出的元素会覆盖掉所在父元素本来具有的原先子元素

v-if和v-for不能在同一元素上联用
v-for执行优先级比v-if高，可能会造成矛盾情况
解决办法：把v-if加到父元素或子元素身上

vue中传入事件对象
使用$event
例子：
<button @click="fun(参数,$event)"></button>
fun(参数,e){
    ......
}


父子组件生命周期执行顺序


nextTick API作用
当vue的dom异步渲染完毕后（vue的dom异步渲染是批量的），执行相应的回调函数

vue2和vue3生命周期区别


vue3组合API
优点：可以把一个功能的代码写在一起，提升了代码可读性和可维护性

vuex
state：
提供唯一的公共数据源，所有共享的数据统一放到store里的state里存储
访问：1.this.$store.state.xx	2.从vuex中导入mapState；映射为computed属性
mutation：
用于变更store中的数据
访问：1.this.$store.commit(mutation方法)	2.从vuex中导入mapMutations；映射为methods方法
action：
用于处理异步任务，但在action中还是通过mutation来修改store中的数据
访问：1.this.$store.dispatch(action方法)	2.从vuex中导入mapActions；映射为methods方法
getters：
用于对store中的数据进行加工处理，形成新的数据
getters不会影响原始数据
访问：1.this.$store.getters.xx		2.从vuex中导入mapGetters；映射为computed属性

为什么要用Vue3 Proxy API 代替Vue2 defineProperty API？
Vue2 defineProperty API 的局限性最大原因是它只能针对单例属性做监听
Vue3 Proxy API 的监听是针对一个对象的，对这个对象的所有操作会进入监听操作，这就完全可以代理所有的属性，会带来很大的性能提升和更优的代码
Vue2 defineProperty API 使用递归遍历对象，把每一层对象数据都变成响应式的，会有很大的性能消耗
Vue3 Proxy API 使得真正访问到的内部属性才会变成响应式，简单地说可以实现按需实现响应式，减少性能消耗

vue路由传参
传参方法1：
this.$router.push("/result?kwd="+this.kwd);
传参方法2：
<router-link to="/result?kwd=this.kwd">查询</router-link>

获取页面路由参数：
this.$route.query

$router和$route区别
$router对象是全局路由route的实例，可在任何组件中访问到
$ruote是访问当前路由信息，包括url，当前路径，参数，query等


vue-router导航钩子
beforeEach  afterEach

router-link和a标签区别
a会跳转到新的页面，router-link不会跳转到新的页面
a会重新渲染页面 router-link不会重新渲染页面


key主要是解决哪⼀类的问题，为什么不建议⽤索引index（重绘）
key的作用主要是为了高效的更新虚拟DOM
为什么不建议用索引index当作key：
当以数组的下标index作为key值时，其中一个元素发生了变化 就有可能导致所有元素的key值发生改变
无论是Vue还是React，当我们在做数组遍历批量生成子节点时，切记同层级的每个子节点的key值不能重复且不会发改变，否则将会产生不可预估的bug。

vue单向数据流
vue的单向数据流（unidirectional data flow）是指用户访问View，View发出用户交互的Action，在Action里对state进行相应更新。 state更新后会触发View更新页面的过程。 这样数据总是清晰的单向进行流动，便于维护并且可以预测。
可以通过store里数据的修改来改变ui，而ui的改变影响不了store中的数据


mvvm框架和mvc框架区别：
mvvm: model+viewModel+view
mvc: model+view+controller
mvvm: 双向数据绑定；mvc：单向数据流

mvvm和mvc最大区别是：mvvm实现了view和model的自动同步，也就是model改变时，view的显示会自动改变
mvc 和 mvvm 其实区别并不大。都是一种设计思想。主要就是 mvc 中 Controller 演变成 mvvm 中的 viewModel。mvvm 主要解决了 mvc 中大量的 DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验。和当 Model 频繁发生变化，开发者需要主动更新到 View 。
