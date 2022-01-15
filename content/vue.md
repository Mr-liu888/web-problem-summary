# [返回主页](https://github.com/Mr-liu888/web-problem-summary/blob/main/README.md)

<b><details><summary>1. 判断当前的运行设备</summary></b>

**1.下载**

```javascript
//npm
npm install current-device

//yarn
yarn add current-device
```
**2.main.js引入**

```javascript
import device from 'current-device'
```
**3.使用**

```javascript
直接调用方法即可

if (device.mobile()) {

  console.log('移动手机')

} else if (device.ipad()) {

  console.log('ipad')

} else if (device.desktop()) {

  console.log('电脑')

}
```
**参考方法(根据自身需求调用和判断)**

<table><thead><tr><th>Device</th><th>JavaScript Method</th></tr></thead><tbody><tr><td>Mobile</td><td>device.mobile()</td></tr><tr><td>Tablet</td><td>device.tablet()</td></tr><tr><td>Desktop</td><td>device.desktop()</td></tr><tr><td>iOS</td><td>device.ios()</td></tr><tr><td>iPad</td><td>device.ipad()</td></tr><tr><td>iPhone</td><td>device.iphone()</td></tr><tr><td>iPod</td><td>device.ipod()</td></tr><tr><td>Android</td><td>device.android()</td></tr><tr><td>Android Phone</td><td>device.androidPhone()</td></tr><tr><td>Android Tablet</td><td>device.androidTablet()</td></tr><tr><td>BlackBerry</td><td>device.blackberry()</td></tr><tr><td>BlackBerry Phone</td><td>device.blackberryPhone()</td></tr><tr><td>BlackBerry Tablet</td><td>device.blackberryTablet()</td></tr><tr><td>Windows</td><td>device.windows()</td></tr><tr><td>Windows Phone</td><td>device.windowsPhone()</td></tr><tr><td>Windows Tablet</td><td>device.windowsTablet()</td></tr><tr><td>Firefox OS</td><td>device.fxos()</td></tr><tr><td>Firefox OS Phone</td><td>device.fxosPhone()</td></tr><tr><td>Firefox OS Tablet</td><td>device.fxosTablet()</td></tr><tr><td>MeeGo</td><td>device.meego()</td></tr><tr><td>Television</td><td>device.television()</td></tr></tbody></table>


</details>

<b><details><summary>2. 在vue项目中通过a标签download下载本地文件</summary></b>

1.将需要下载的文件放在public，也就是和index.html文件一个文件夹下即可，如下图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/3240a09151dd4dd89ac82424af770cc0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA54ix54Sw,size_20,color_FFFFFF,t_70,g_se,x_16)
然后在需要进行点击下载文件的地方添加如下代码：

```javascript
<a href="./需要下载的文件名" download>点击下载</a>
```
就可以实现下载啦。

</details>

<b><details><summary>3. 项目的 env 文件使用</summary></b>

这个文件的产生是为了区分各个开发环境...

文件名的解释：

文件(在项目根目录新建)
.env 无论开发环境还是生成环境都会加载
.env.development 开发环境加载这个文件
.env.production 生成环境加载这个文件

**注意**
env 文件需要声明运行的环境



```javascript
.env.development
NODE_ENV = development
---------------------------------------------------------
.env.production
NODE_ENV = production
```
定义变量需要以 VUE_APP_ 作为前缀
例如：

```javascript
.env.development
NODE_ENV = development
VUE_APP_BASE_URL = http://dev.myhost.co
---------------------------------------------------------
.env.production
NODE_ENV = production
VUE_APP_BASE_URL = http://www.myhost.com
```
测试变量是否生效, 可直接在 main.js 中打印测试

```javascript
console.log(process.env.VUE_APP_BASE_URL);
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/05147abd2859447ea70904de1a26d624.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA54ix54Sw,size_20,color_FFFFFF,t_70,g_se,x_16)


</details>

<b><details><summary>4. clipboard实现文本复制</summary></b>

**1.下载**

```javascript
npm install clipboard --save
版本："^2.0.4"  
```
**2.引入使用**

```javascript
import Clipboard from "clipboard";
```
**3.使用方法**

```javascript
   <el-button
      id="publicKey"
       type="success"
       :data-clipboard-text="linkUrl"
       @click="copy('publicKey')"
   >
    Copy linkUrl
   </el-button>
---------------------------------------------------------
  data() {
    return {
       linkUrl: 'www.baidu.com'
    },
    methods:{
      copy(type) {
	      if (!this.linkUrl) {
	        this.$message({
	          message: "linkUrl is empty",
	          type: "error",
	        });
	      } else {
	        var clipboard = new Clipboard(`#${type}`);
	        clipboard.on("success", (e) => {
	          // 释放内存
	          clipboard.destroy();
	          this.$message({
	            message: "Copy successful",
	            type: "success",
	          });
	        });
	        clipboard.on("error", (e) => {
	          // 不支持复制
	          this.$message.error("The browser does not support quick copy");
	          // 释放内存
	          clipboard.destroy();
	        });
	      }
	    }
     }
```


</details>

<b><details><summary>5. postcss-px-to-viewport移动端适配插件</summary></b>

之前做移动端适配时，基本上是采用rem方案，现在发现了一个新的方案，就是用viewport单位，现在viewport单位越来越受到众多浏览器的支持，postcss-px-to-viewport，将px单位自动转换成viewport单位，用起来超级简单。

**1.安装**

```javascript
npm install postcss-px-to-viewport --save-dev
```

**2.在vue.config.js中配置**

```javascript
module.exports = {
  css: {
    // 将项目和插件中的px转成rem
    loaderOptions: {
      postcss: {
        plugins: [
          require('postcss-px-to-viewport')({
            unitToConvert: 'px',  // 要转换的单位，默认是'px'
            viewportWidth: 375, // 视窗的宽度，对应的是我们设计稿的宽度，一般是375
            unitPrecision: 3,   // 指定`px`转换为视窗单位值的小数位数
            propList: ['*'],  // 指定可以转换的css属性，默认是['*']，代表全部属性进行转换
            viewportUnit: 'vw',  //指定需要转换成的视窗单位，建议使用vw
            fontViewportUnit: 'vw', // 指定字体需要转换成的视窗单位，默认vw
            selectorBlackList: ['.pc-', '.van-'], // 指定不转换为视窗单位的类，可以自定义，可以无限添加,建议定义一至两个通用的类名
            minPixelValue: 1, // 小于或等于`1px`不转换为视窗单位，你也可以设置为你想要的值
            mediaQuery: false, // 允许在媒体查询中转换`px`
            exclude: [/node_modules/]// 设置忽略文件，用正则做目录名匹配
          })
        ]
      }
    }
  }
}
```
3.项目源码：

```javascript
https://gitee.com/english-sunflower/vue-vant-element.git
项目使用了postcss-px-to-viewport插件，并集成了elenentUI和vantUI，完美兼容pc端和移动端
```


</details>

<b><details><summary>6. 三种方法重置vue组件的data数据</summary></b>

我们在vue组件中经常遇到需要重置表单的场景，需要重置data中的对象，下面三种方法，帮你简单完成。

**1. 方法一:element的resetfields**

```javascript
this.$refs[formRef].resetfields()
```
**2.方法二-vue的thisoptionsdataform方法对form重置**

```javascript
this.form = this.$options.data().form
```

**3.方法三-vue的data重置**

```javascript
this.$data = this.$options.data();
```



</details>

<b><details><summary>7. vue中8种组件通信方式,纯干货！值得收藏</summary></b>

vue是数据驱动视图更新的框架, 所以对于vue来说组件间的数据通信非常重要，那么组件之间如何进行数据通信的呢？
首先我们需要知道在vue中组件之间存在什么样的关系, 才更容易理解他们的通信方式, 就好像过年回家，坐着一屋子的陌生人，相互之间怎么称呼，这时就需要先知道自己和他们之间是什么样的关系。
vue组件中关系说明:

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190722093404290.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0Ffc291bG1hdGU=,size_16,color_FFFFFF,t_70)
如上图所示, A与B、A与C、B与D、C与E组件之间是父子关系； B与C之间是兄弟关系；A与D、A与E之间是隔代关系； D与E是堂兄关系（非直系亲属） 针对以上关系我们归类为：

- 父子组件之间通信
- 非父子组件之间通信(兄弟组件、隔代关系组件等)


本文会介绍组件间通信的8种方式如下图目录所示:并介绍在不同的场景下如何选择有效方式实现的组件间通信方式，希望可以帮助小伙伴们更好理解组件间的通信。

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019072209371934.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0Ffc291bG1hdGU=,size_16,color_FFFFFF,t_70)

    一、props / $emit

父组件通过`props`的方式向子组件传递数据，而通过`$emit` 子组件可以向父组件通信。

**1. 父组件向子组件传值**

下面通过一个例子说明父组件如何向子组件传递数据：在子组件`article.vue`中如何获取父组件`section.vue`中的数据`articles:['红楼梦', '西游记','三国演义']`

    // section父组件
    <template>
      <div class="section">
        <com-article :articles="articleList"></com-article>
      </div>
    </template>
    
    <script>
    import comArticle from './test/article.vue'
    export default {
      name: 'HelloWorld',
      components: { comArticle },
      data() {
        return {
          articleList: ['红楼梦', '西游记', '三国演义']
        }
      }
    }
    </script>



    // 子组件 article.vue
    <template>
      <div>
        <span v-for="(item, index) in articles" :key="index">{{item}}</span>
      </div>
    </template>
    
    <script>
    export default {
      props: ['articles']
    }
    </script>


总结: prop 只可以从上一级组件传递到下一级组件（父子组件），即所谓的单向数据流。而且 prop 只读，不可被修改，所有修改都会失效并警告。

**2. 子组件向父组件传值**

对于`$emit` 我自己的理解是这样的: `$emit`绑定一个自定义事件, 当这个语句被执行时, 就会将参数`arg`传递给父组件,父组件通过`v-on`监听并接收参数。 通过一个例子，说明子组件如何向父组件传递数据。
在上个例子的基础上, 点击页面渲染出来的`ariticle`的`item`, 父组件中显示在数组中的下标


    // 父组件中
    <template>
      <div class="section">
        <com-article :articles="articleList" @onEmitIndex="onEmitIndex"></com-article>
        <p>{{currentIndex}}</p>
      </div>
    </template>
    
    <script>
    import comArticle from './test/article.vue'
    export default {
      name: 'HelloWorld',
      components: { comArticle },
      data() {
        return {
          currentIndex: -1,
          articleList: ['红楼梦', '西游记', '三国演义']
        }
      },
      methods: {
        onEmitIndex(idx) {
          this.currentIndex = idx
        }
      }
    }
    </script>


    // 子组件中
        <template>
          <div>
            <div v-for="(item, index) in articles" :key="index" @click="emitIndex(index)">{{item}}</div>
          </div>
        </template>
        
        <script>
        export default {
          props: ['articles'],
          methods: {
            emitIndex(index) {
              this.$emit('onEmitIndex', index)
            }
          }
        }
        </script>


**二、 $children / $parent**

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019072210243260.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0Ffc291bG1hdGU=,size_16,color_FFFFFF,t_70)

上面这张图片是vue官方的解释，通过`$parent`和`$children`就可以访问组件的实例，拿到实例代表什么？代表可以访问此组件的所有方法和data。接下来就是怎么实现拿到指定组件的实例。

**使用方法**

    // 父组件中
    <template>
      <div class="hello_world">
        <div>{{msg}}</div>
        <com-a></com-a>
        <button @click="changeA">点击改变子组件值</button>
      </div>
    </template>
    
    <script>
    import ComA from './test/comA.vue'
    export default {
      name: 'HelloWorld',
      components: { ComA },
      data() {
        return {
          msg: 'Welcome'
        }
      },
    
      methods: {
        changeA() {
          // 获取到子组件A
          this.$children[0].messageA = 'this is new value'
        }
      }
    }
    </script>


    // 子组件中
    <template>
      <div class="com_a">
        <span>{{messageA}}</span>
        <p>获取父组件的值为:  {{parentVal}}</p>
      </div>
    </template>
    
    <script>
    export default {
      data() {
        return {
          messageA: 'this is old'
        }
      },
      computed:{
        parentVal(){
          return this.$parent.msg;
        }
      }
    }
    </script>


要注意边界情况，如在`#app`上拿`$parent`得到的是`new Vue()`的实例，在这实例上再拿`$parent`得到的是`undefined`，而在最底层的子组件拿`$children`是个空数组。也要注意得到`$parent`和`$children`的值不一样，`$children` 的值是数组，而`$parent`是个对象

**总结**

上面两种方式用于父子组件之间的通信， 而使用props进行父子组件通信更加普遍; 二者皆不能用于非父子组件之间的通信。

**三、provide/ inject**

**概念:**

`provide/ inject` 是vue2.2.0新增的api, 简单来说就是父组件中通过`provide`来提供变量, 然后再子组件中通过`inject`来注入变量。

**注意:** 这里不论子组件嵌套有多深, 只要调用了`inject` 那么就可以注入`provide`中的数据，而不局限于只能从当前父组件的`props`属性中回去数据

**举例验证**

接下来就用一个例子来验证上面的描述: 假设有三个组件: A.vue、B.vue、C.vue 其中 C是B的子组件，B是A的子组件



    // A.vue
    
    <template>
      <div>
    	<comB></comB>
      </div>
    </template>
    
    <script>
      import comB from '../components/test/comB.vue'
      export default {
        name: "A",
        provide: {
          for: "demo"
        },
        components:{
          comB
        }
      }
    </script>



    // B.vue
    
    <template>
      <div>
        {{demo}}
        <comC></comC>
      </div>
    </template>
    
    <script>
      import comC from '../components/test/comC.vue'
      export default {
        name: "B",
        inject: ['for'],
        data() {
          return {
            demo: this.for
          }
        },
        components: {
          comC
        }
      }
    </script>


    // C.vue
    <template>
      <div>
        {{demo}}
      </div>
    </template>
    
    <script>
      export default {
        name: "C",
        inject: ['for'],
        data() {
          return {
            demo: this.for
          }
        }
      }
    </script>

**四、ref / refs**

`ref`：如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例，可以通过实例直接调用组件的方法或访问数据， 我们看一个`ref` 来访问组件的例子:

    // 子组件 A.vue
    
    export default {
      data () {
        return {
          name: 'Vue.js'
        }
      },
      methods: {
        sayHello () {
          console.log('hello')
        }
      }
    }

    // 父组件 app.vue
    
    <template>
      <component-a ref="comA"></component-a>
    </template>
    <script>
      export default {
        mounted () {
          const comA = this.$refs.comA;
          console.log(comA.name);  // Vue.js
          comA.sayHello();  // hello
        }
      }
    </script>

**五、eventBus**

**eventBus** 又称为事件总线，在vue中可以使用它来作为沟通桥梁的概念, 就像是所有组件共用相同的事件中心，可以向该中心注册发送事件或接收事件， 所以组件都可以通知其他组件。

*eventBus也有不方便之处, 当项目较大,就容易造成难以维护的灾难*

在Vue的项目中怎么使用eventBus来实现组件之间的数据通信呢?具体通过下面几个步骤

**1. 初始化**

首先需要创建一个事件总线并将其导出, 以便其他模块可以使用或者监听它.

    // event-bus.js
    
    import Vue from 'vue'
    export const EventBus = new Vue()

**2. 发送事件**

假设你有两个组件: `additionNum` 和 `showNum`, 这两个组件可以是兄弟组件也可以是父子组件；这里我们以兄弟组件为例:

    <template>
      <div>
        <show-num-com></show-num-com>
        <addition-num-com></addition-num-com>
      </div>
    </template>
    
    <script>
    import showNumCom from './showNum.vue'
    import additionNumCom from './additionNum.vue'
    export default {
      components: { showNumCom, additionNumCom }
    }
    </script>



    // addtionNum.vue 中发送事件
    
    <template>
      <div>
        <button @click="additionHandle">+加法器</button>    
      </div>
    </template>
    
    <script>
    import {EventBus} from './event-bus.js'
    console.log(EventBus)
    export default {
      data(){
        return{
          num:1
        }
      },
    
      methods:{
        additionHandle(){
          EventBus.$emit('addition', {
            num:this.num++
          })
        }
      }
    }
    </script>


**3. 接收事件**

    // showNum.vue 中接收事件
    
    <template>
      <div>计算和: {{count}}</div>
    </template>
    
    <script>
    import { EventBus } from './event-bus.js'
    export default {
      data() {
        return {
          count: 0
        }
      },
    
      mounted() {
        EventBus.$on('addition', param => {
          this.count = this.count + param.num;
        })
      }
    }
    </script>

这样就实现了在组件`addtionNum.vue`中点击相加按钮, 在`showNum.vue`中利用传递来的	`num` 展示求和的结果.

**4. 移除事件监听者**

如果想移除事件的监听, 可以像下面这样操作:

    import { eventBus } from 'event-bus.js'
    EventBus.$off('addition', {})

**六、Vuex**

**1.  Vuex介绍**

Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化.
Vuex 解决了多个视图依赖于同一状态和来自不同视图的行为需要变更同一状态的问题，将开发者的精力聚焦于数据的更新而不是数据在组件之间的传递上

**2. Vuex各个模块**

1. *state*：用于数据的存储，是store中的唯一数据源
2. *getters*：如vue中的计算属性一样，基于state数据的二次包装，常用于数据的筛选和多个数据的相关性计算
3. *mutations*：类似函数，改变state数据的唯一途径，且不能用于处理异步事件
4. *actions*：类似于mutation，用于提交mutation来改变状态，而不直接变更状态，可以包含任意异步操作
5. *modules*：类似于命名空间，用于项目中将各个模块的状态分开定义和操作，便于维护


	    // 父组件
	    
	    <template>
	      <div id="app">
	        <ChildA/>
	        <ChildB/>
	      </div>
	    </template>
	    
	    <script>
	      import ChildA from './components/ChildA' // 导入A组件
	      import ChildB from './components/ChildB' // 导入B组件
	    
	      export default {
	        name: 'App',
	        components: {ChildA, ChildB} // 注册A、B组件
	      }
	    </script>


	    // 子组件childA
	    
	    <template>
	      <div id="childA">
	        <h1>我是A组件</h1>
	        <button @click="transform">点我让B组件接收到数据</button>
	        <p>因为你点了B，所以我的信息发生了变化：{{BMessage}}</p>
	      </div>
	    </template>
	    
	    <script>
	      export default {
	        data() {
	          return {
	            AMessage: 'Hello，B组件，我是A组件'
	          }
	        },
	        computed: {
	          BMessage() {
	            // 这里存储从store里获取的B组件的数据
	            return this.$store.state.BMsg
	          }
	        },
	        methods: {
	          transform() {
	            // 触发receiveAMsg，将A组件的数据存放到store里去
	            this.$store.commit('receiveAMsg', {
	              AMsg: this.AMessage
	            })
	          }
	        }
	      }
	    </script>
	    


	    // 子组件 childB
	    
	    <template>
	      <div id="childB">
	        <h1>我是B组件</h1>
	        <button @click="transform">点我让A组件接收到数据</button>
	        <p>因为你点了A，所以我的信息发生了变化：{{AMessage}}</p>
	      </div>
	    </template>
	    
	    <script>
	      export default {
	        data() {
	          return {
	            BMessage: 'Hello，A组件，我是B组件'
	          }
	        },
	        computed: {
	          AMessage() {
	            // 这里存储从store里获取的A组件的数据
	            return this.$store.state.AMsg
	          }
	        },
	        methods: {
	          transform() {
	            // 触发receiveBMsg，将B组件的数据存放到store里去
	            this.$store.commit('receiveBMsg', {
	              BMsg: this.BMessage
	            })
	          }
	        }
	      }
	    </script>

vuex的`store,js`

    import Vue from 'vue'
    import Vuex from 'vuex'
    Vue.use(Vuex)
    const state = {
      // 初始化A和B组件的数据，等待获取
      AMsg: '',
      BMsg: ''
    }
    
    const mutations = {
      receiveAMsg(state, payload) {
        // 将A组件的数据存放于state
        state.AMsg = payload.AMsg
      },
      receiveBMsg(state, payload) {
        // 将B组件的数据存放于state
        state.BMsg = payload.BMsg
      }
    }
    
    export default new Vuex.Store({
      state,
      mutations
    })

**七、localStorage / sessionStorage**

这种通信比较简单,缺点是数据和状态比较混乱,不太容易维护。 通过`window.localStorage.getItem(key)`获取数据 通过`window.localStorage.setItem(key,value)`存储数据

注意用`JSON.parse() / JSON.stringify()` 做数据格式转换 `localStorage / sessionStorage`可以结合`vuex`, 实现数据的持久保存,同时使用`vuex`解决数据和状态混乱问题.

**八 $attrs与 $listeners**

现在我们来讨论一种情况， 我们一开始给出的组件关系图中A组件与D组件是隔代关系， 那它们之前进行通信有哪些方式呢？

1. 使用`props`绑定来进行一级一级的信息传递, 如果D组件中状态改变需要传递数据给A, 使用事件系统一级级往上传递
2. 使用`eventBus`,这种情况下还是比较适合使用, 但是碰到多人合作开发时, 代码维护性较低, 可读性也低
3. 使用`Vuex`来进行数据管理, 但是如果仅仅是传递数据, 而不做中间处理,使用Vuex处理感觉有点大材小用了.


在vue2.4中，为了解决该需求，引入了`$attrs` 和`$listeners` ， 新增了`inheritAttrs` 选项。 在版本2.4以前，默认情况下,父作用域中不作为 `prop` 被识别 (且获取) 的特性绑定 (class 和 style 除外)，将会“回退”且作为普通的HTML特性应用在子组件的根元素上。接下来看一个跨级通信的例子:


    // app.vue
    // index.vue
    
    <template>
      <div>
        <child-com1
          :name="name"
          :age="age"
          :gender="gender"
          :height="height"
          title="程序员成长指北"
        ></child-com1>
      </div>
    </template>
    <script>
    const childCom1 = () => import("./childCom1.vue");
    export default {
      components: { childCom1 },
      data() {
        return {
          name: "zhang",
          age: "18",
          gender: "女",
          height: "158"
        };
      }
    };
    </script>
    

    // childCom1.vue
    
    <template class="border">
      <div>
        <p>name: {{ name}}</p>
        <p>childCom1的$attrs: {{ $attrs }}</p>
        <child-com2 v-bind="$attrs"></child-com2>
      </div>
    </template>
    <script>
    const childCom2 = () => import("./childCom2.vue");
    export default {
      components: {
        childCom2
      },
      inheritAttrs: false, // 可以关闭自动挂载到组件根元素上的没有在props声明的属性
      props: {
        name: String // name作为props属性绑定
      },
      created() {
        console.log(this.$attrs);
         // { "age": "18", "gender": "女", "height": "158", "title": "程序员成长指北" }
      }
    };
    </script>



    // childCom2.vue
    
    <template>
      <div class="border">
        <p>age: {{ age}}</p>
        <p>childCom2: {{ $attrs }}</p>
      </div>
    </template>
    <script>
    
    export default {
      inheritAttrs: false,
      props: {
        age: String
      },
      created() {
        console.log(this.$attrs); 
        // { "gender": "女", "height": "158", "title": "程序员成长指北" }
      }
    };
    </script>


**总结**
常见使用场景可以分为三类:

父子组件通信: `props`; `$parent / $children`; `provide / inject` ; `ref` ;  `$attrs / $listeners`
兄弟组件通信: `eventBus` ; `vuex`
跨级通信:  `eventBus`；`Vuex`；`provide / inject` 、`$attrs / $listeners`


</details>

<b><details><summary>8. vue实现word或pdf文档导出的功能，干货！</summary></b>

vue实现word或pdf文档导出的功能，我的项目是：后端返回一个文档流(下图)，然后前端对文档流做处理进行下载，代码如下：

    import axios from 'axios';
    
            axios.get(`url`, { //url: 接口地址
    
              responseType: `arraybuffer` //一定要写
    
            })
    
              .then(res => {
    
                if (res.status == 200) {
    
                  let blob = new Blob([res.data], {
    
                    type: `application/msword` //word文档为msword,pdf文档为pdf，msexcel 为excel
    
                  });
    
                  let objectUrl = URL.createObjectURL(blob);
    
                  let link = document.createElement("a");
    
                  let fname = `我的文档.doc`; //下载文件的名字+后缀名
    
                  link.href = objectUrl;
    
                  link.setAttribute("download", fname);
    
                  document.body.appendChild(link);
    
                  link.click();
    
                } else {
    
                  this.$message({
    
                    type: "error",
    
                    message: "导出失败"
    
                  })
    
                }
    
              });


</details>

<b><details><summary>9. Vue中获取要操作的元素DOM，怎样搞定？</summary></b>

在使用Vue的时候，有时候我们希望直接用Js操纵DOM来实现某些效果，具体实现只用利用Vue提供的ref属性以及this.$refs即可实现。下面放一个小DEMO！

    <!DOCTYPE html>
    <html>
     
    	<head>
    		<meta charset="utf-8">
    		<title>Examples</title>
    		<style>
    			.box{width: 200px;height: 200px;border: 1px solid #f00;}
    		</style>
    		<script type="text/javascript" src="js/vue.js" ></script>
    	</head>
     
    	<body>
    		<div id="app">
    			<div ref='box' class="box" v-on:click="changeText()">这是一个盒子</div>
    		</div>
     
    		<script>
    			var app = new Vue({
    				el: '#app',
    				data: {
    					msg: ""
    				},
    				methods: {
     
    					changeText: function() {
    						this.$refs.box.innerHTML = "改变盒子的文字";
    					}
     
    				}
    			})
    		</script>
     
    	</body>
     
    </html>


</details>
