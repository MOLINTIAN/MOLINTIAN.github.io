

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
orderBy   v-for ="val in arr | orderBy '1' " 1正序，-1逆序
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
