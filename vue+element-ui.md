

vue中跳转用的是this.$router.push({path:'lujing'})

v-model是赋值对象。

v-for = "item in msgdata" 循环magdate的数据。数组中有重复数据  track-by="$index/uid" 也会提高效率。

v-show是动态的v-if判断，而且v-show相比v-if更加适用，如果两个出现矛盾，可以尝试两者更换。

unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。this.msgdata.unshift(){}

向msgdata中添加数据：this.msg.push();利用push添加。

网速慢的时候，{{}}用户会看到闪烁。v-cloak 防止闪烁，样式中：[v-cloak]{display:none}

v-text是用于操作纯文本，它会替代显示对应的数据对象上的值,此处为单向绑定.它的简写为：{{}}，防止闪烁

v-html用于输出html,v-html会将其当html标签解析后输出。解析标签。解析标签。v-html="msg"

v-model通常用于表单组件的绑定，例如input，select等。它与v-text的区别在于它实现的表单组件的双向绑定，如果用于表单控件以外标签是没有用的。

{{{}}}三个花括号，转义，现在已经不用，防止闪烁

计算属性的使用：computed：{业务逻辑代码}

Vue选项的合并之$options

vue提供的过滤器：
capitalize,uppercase,currency
过滤器：debounce  延迟执行

和数组配合使用的过滤器：arr=['wo'，'ni','ta']

limitBy限制几个/限制取出几个/从几个开始取，取几个/ v-for ="val in arr | limitBy 2 1 "

filterBy  v-for ="val in arr | filterBy 'w' " 

orderBy   v-for ="val in arr | orderBy '1' " 1正序，-1逆序，2倒叙

model到view的过程，read和wirte

自定义过滤器：
Vue.filter('name',function(input,a,b){})
例子：时间转化器 
<div>
  {{a | date}}
</div>
<script>
  Vue.filter('date',function(input){
  var oDate=new Date(input);
  return oDate.getFullYear（）+'-'+(oDate.getMonth()+1)+'-'+oDate.getDate()+'-'+oDate.getHours()+':'+Odate.getMinutes()+':'+
  oDate.getSeconds();
  });
  var vm=new Vue({
  data:{
  a:Date.now()
  }
  methods:{}
  }).$mount('#box');
</script>

$mount()手动挂载
当Vue实例没有el属性时，则该实例尚没有挂载到某个dom中；
假如需要延迟挂载，可以在之后手动调用vm.$mount()方法来挂载。

双向过滤器：

vue事件 @click
el绑定，可以是'#id'，可以使'.class'。
@keydown/keyup   @keydown.up/@keydown,down    event绑定keycode

vue交互  vue-resourses.js是实现交互的配置文件  
resources+ajax+php:
发送请求：

this.$http.get()/post()/jsonp()

this.$http({

url:地址,

data:给后台提交的数据,

method:'get'/'post'/'json'

jsonp:'cd'//cdname

}).then(function(res){

var json = res.data

})

vue的生存周期，
钩子函数：
created：实例已经创建，执行

beforeCompile:编译之前

compiled：编译之后（创建到dom树上）

ready 加载完实现

beforeDestory:销毁之前

destoryed:销毁之后

自定义指令：Vue.directive('red',function(){this.el.style.background = 'red'})v-red 是指令名称，在定义的时候去掉v-
this.el是原生的DOM对象。

自定义键盘信息：Vue.directive('on').keyCode.Ctrl=17

延迟执行：@keydown.enter="show | debounce 2000"

监听数据变化：vm.$el/$mount/$option/...

vm.$watch(name,fnCb)；浅度监听数据变化。fnCb是函数

vm.$watch(name,fnCb，{deep:true})；深度监听数据变化。

vue过渡动画：本质走的是css3:transition,animation
推荐使用animate.css来做动画。

动画最简洁的形式：
.fade-transition{transition:1s all ease;}
进入：
.fade.enter{opacty:0;}
离开：
.fade-leave{opacity:0;transform:translateX(200px);}

vue组件（重要）

slot:作用：占个位置

vue-resource:交互;vue-router:路由;根据不同的url，出现不同的效果。

vue中路由：<a v-link="{path:'/home'}">主页</a>,跳转用的v-link,在v-router中定义好路径，可多层嵌套路由。

展示内容：<router-view></router-view>（路径访问后需要加上）

路由中的其他信息：
拼接路由：

去路由中的信息：$router.param,取出路由中的参数。$router.path，当前的路径。$router.query.当前路由的数据。

vue-loader:是基于webpack,模块加载器，在这里一切都是模块。网页是不识别.vue文件的，必须使用加载器来起作用。

vue文件的结构：<template></template><script></script><style></sytle>

简单的目录结构：index.html，main.js(入口文件)，App.vue(vue文件，推荐大写)，package.json(工程依赖文件,里面定义了传输格式等。)，webpack.config.js(webpack配置文件)

build.js出口文件定义。

模块化开发：
导出模块：expert default{}

引入模块：import 模块名 from 地址。

webpack的准备工作：安装webpack和webpack-dev-server在node_modules中)

vue-loader：vue-html-loader（解析tempalte）;vue-style-loader(解析style)；

脚手架vue-cli:帮你提供一个基本的项目结构，本身集成了很多的项目模板：webpack和webpacksimple。

基本使用流程：

1，安装命令：npm install vue-cli-g

2，生成项目模板：vue-init <模板名>
