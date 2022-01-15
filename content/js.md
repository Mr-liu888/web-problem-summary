# [返回主页](https://github.com/Mr-liu888/web-problem-summary/blob/main/README.md)

<b><details><summary>1. 数组怎么根据另一个数组筛选数据，并提取出来？</summary></b>

第一个数组：

```javascript
let comments = [
	{
	    id：1，
	    name: 'A_soulmate',
	    message: ' nice day',
	    dateTime: '2022-01-13'
	},
	{
	    id：2，
	    name: 'A_soulmate2',
	    message: 'nice day',
	    dateTime: '2022-01-13
	},
	{ 
	    id：3，
	    name: 'A_soulmate3',
	    message: 'nice day',
	    dateTime: '2022-01-13'
	},
	{
	    id：4，
	    name: 'A_soulmate4',
	    message: 'nice day',
	    dateTime: '2022-01-13'
	}
]
```

第二个数组

```javascript
let number=[1,2];
```
**comments 数组如何根据自身id对应number数组的值筛选并提取？**

```javascript
let filtered = comments.filter(comment => number.indexOf(comment.id) !== -1);
console.log(filtered);
或者
let filterArr=comments.filter(item=>{return number.includes(item.id)})
console.log(filterArr)
```

</details>

<b><details><summary>2. form-data向后台传输数组</summary></b>

原本的数据：

```javascript
let data = {
            id_list:[23652,59845]
        }
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/dde683a1c479410186b978ff1def9e5c.png)
很明显这样不能变成数组，所以要变化一种形式写。

```javascript
let data = {
            id_list:JSON.stringify([23652,59845])
        }
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/5834ae8027654c44ae8298c1c5a2f9c0.png)
这样写就可以了！


</details>

<b><details><summary>3. 金额数目千分位显示</summary></b>

**问题描述**
应用中金钱数目常常使用千分位分隔，使用js写了一个简单的函数。

**解决方案**
可以使用字符串操作，也可以数组操作，不过最简单的还是正则替换。

分了2种情况，一种是以1234567为例子，先字符串截取得到前面的1，然后对后面的234和567替换为’,234’与’,567’，然后拼接得到1,234,567。另一中是位数刚好是3的倍数的，比如123456789，然后替换得到’,123,456,789’，然后字符串截取得到123,456,789。

```javascript
function get_thousand_num(num) {
    return (num || 0).toString().replace(/\d+/, function (n) {
        var len = n.length;
        if (len % 3 === 0) {
            return n.replace(/(\d{3})/g, ',$1').slice(1);
        } else {
            return n.slice(0, len % 3) + n.slice(len % 3).replace(/(\d{3})/g, ',$1');
        }
    });
}
```

</details>

<b><details><summary>4. 将毫秒转换成“天时分秒“</summary></b>

话不多说，直接上代码开搞。

```javascript
formatTime(msTime) {

    let time = msTime /1000;

    let day = Math.floor(time /60 /60 /24);

    let hour = Math.floor(time /60 /60) %24;

    let minute = Math.floor(time /60) %60;

    let second = Math.floor(time) %60;

    return `${day}天${hour}时${minute}分${second}秒`

}
```


</details>

<b><details><summary>5. 获取文件名和后缀名称</summary></b>

1.使用subtring() 截取字符串，对于文件名中会出现多个点的很有用，从最后一个点的地方截取。

```javascript
// 获取文件名
getFileName (name) {
      return name.substring(0, name.lastIndexOf("."))
},
// 获取 .后缀名
getExtension (name) {
      return name.substring(name.lastIndexOf("."))
}
// 只获取后缀名
getExtension (name) {
      return name.substring(name.lastIndexOf(".")+1)
}
```
2.使用正则，对只会出现一个点的适用

```javascript
表达式为：([^\\/]+)\.([^\\/]+)

<script type="text/javascript">
    var a="c:\\windows\\abc.txt";
    var reg = /([^\\/]+)\.([^\\/]+)/i;
    reg.test(a);
    alert(RegExp.$1);
    alert(RegExp.$2);
</script>
```


</details>

<b><details><summary>6. 7个有用JavaScript技巧</summary></b>
<div class="blog-content-box">
    <div class="article-header-box">
        <div class="article-header">
            <div class="article-title-box">
                 <h1 class="title-article"></h1>
            </div>
            <div class="article-info-box">
                <div class="article-bar-top" style="height: 24px;">
                                                                                                                        <span class="time"></span>
                    <a class="follow-nickName" href="https://me.csdn.net/qq_43258252" target="_blank"></a>
                    <span class="read-count"></span><span class="article_info_click" style="position: static;"></span>
                                                                                                <div class="tags-box space">
                                <span class="label"></span>
                                                                <a class="tag-link" href="" target="_blank">                                                                    </a>
                            </div>
                                                                                    </div>
                <div class="operating">
                                    </div>
            </div>
        </div>
    </div>
    <article class="baidu_pl">
                <div id="article_content" class="article_content clearfix" data-track-view="{&quot;mod&quot;:&quot;popu_307&quot;,&quot;con&quot;:&quot;,https://blog.csdn.net/qq_43258252/article/details/94737380,&quot;}" data-track-click="{&quot;mod&quot;:&quot;popu_307&quot;,&quot;con&quot;:&quot;,https://blog.csdn.net/qq_43258252/article/details/94737380&quot;}">
                                                <div class="article-copyright">
                <span class="creativecommons">
                <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
                   </a>
            <span></span><a href="http://creativecommons.org/licenses/by-sa/4.0/"></a>
            </span>
                    </div>
                                                    <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-3019150162.css">
                                        <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-3019150162.css">
                <div class="htmledit_views" id="content_views">
                                            <h2 id="articleHeader1"><a name="t0"></a>数组去重</h2>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">var</span> arr = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>];</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(...new <span class="hljs-built_in">Set</span>(arr))</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    &gt;&gt; [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>]</div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<h2 id="articleHeader2"><a name="t1"></a>数组和布尔</h2>

<p>有时我们需要过滤数组中值为&nbsp;<code>false</code>&nbsp;的值. 例如(<code>0</code>,&nbsp;<code>undefined</code>,&nbsp;<code>null</code>,&nbsp;<code>false</code>), 你可能不知道这样的技巧</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> <span class="hljs-keyword">var</span> myArray = [<span class="hljs-number">1</span>, <span class="hljs-number">0</span> , <span class="hljs-literal">undefined</span>, <span class="hljs-literal">null</span>, <span class="hljs-literal">false</span>];</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> myArray.filter(<span class="hljs-built_in">Boolean</span>);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> &gt;&gt; [<span class="hljs-number">1</span>]</div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p>是不是很简单, 只需要传入一个&nbsp;<code>Boolean</code>&nbsp;函数即可.</p>

<h2 id="articleHeader3"><a name="t2"></a>创建一个空对象</h2>

<p>有时我们需要创建一个纯净的对象, 不包含什么原型链等等. 一般创建空对象最直接方式通过字面量&nbsp;<code>{}</code>, 但这个对象中依然存在&nbsp;<code>__proto__</code>&nbsp;属性来指向 Object.prototype 等等.</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">let</span> dict = <span class="hljs-built_in">Object</span>.create(<span class="hljs-literal">null</span>);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    dict.__proto__ === <span class="hljs-string">"undefined"</span> </div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<h2 id="articleHeader4"><a name="t3"></a>合并对象</h2>

<p>在JavaScript中合并多个对象的需求一直存在, 比如在传参时需要把表单参数和分页参数进行合并后在传递给后端</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> page = {</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">        <span class="hljs-attr">current</span>: <span class="hljs-number">1</span>,</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">        <span class="hljs-attr">pageSize</span>: <span class="hljs-number">10</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    }</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="5"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="6"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> form = {</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="7"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">        <span class="hljs-attr">name</span>: <span class="hljs-string">""</span>,</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="8"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">        <span class="hljs-attr">sex</span>: <span class="hljs-string">""</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="9"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    }</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="10"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="11"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> params = {...form, ...page};</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="12"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="13"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment"><span class="hljs-comment">/*</span></span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="14"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">        {</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="15"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">            name: "",</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="16"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">            sex: "",</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="17"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">            current: 1,</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="18"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">            pageSize: 10</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="19"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment"></span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="20"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">        }</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="21"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"><span class="hljs-comment">    *</span></div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p>利用ES6提供的扩展运算符让对象合并变得很简单.</p>

<h2 id="articleHeader5"><a name="t4"></a>函数参数必须</h2>

<p>ES6中可以给参数指定默认值,确实带来很多便利. 如果需要检测某些参数是必传时,可以这么做</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> isRequired = <span class="hljs-function"><span class="hljs-params">()</span> =&gt;</span> { <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> <span class="hljs-built_in">Error</span>(<span class="hljs-string">'param is required'</span>); };</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> hello = <span class="hljs-function">(<span class="hljs-params">name = isRequired(</span>)) =&gt;</span> { <span class="hljs-built_in">console</span>.log(<span class="hljs-string">`hello <span class="hljs-subst">${name}</span>`</span>) };</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="5"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// 这里将抛出一个错误,因为名字时必须</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="6"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    hello();</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="7"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// 这也将抛出一个错误</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="8"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    hello(<span class="hljs-literal">undefined</span>);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="9"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="10"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// 正常</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="11"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    hello(<span class="hljs-literal">null</span>);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="12"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    hello(<span class="hljs-string">'David'</span>); </div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<h2 id="articleHeader6"><a name="t5"></a>解构赋值时使用别名</h2>

<p>解构赋值是一个非常受欢迎的JavaScript功能，但有时我们更喜欢用其他名称引用这些属性，所以我们可以利用别名来完成:</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> obj = { <span class="hljs-attr">x</span>: <span class="hljs-number">1</span> };</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// Grabs obj.x as { x }</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="5"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> { x } = obj;</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="6"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="7"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// Grabs obj.x as { otherName }</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="8"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">const</span> { <span class="hljs-attr">x</span>: otherName } = obj;</div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<h2 id="articleHeader7"><a name="t6"></a>获取查询参数</h2>

<p>多年来，我们编写粗糙的正则表达式来获取查询字符串值，但那些日子已经一去不复返了; 现在我们可以通过&nbsp;<code>URLSearchParams</code>&nbsp;API 来获取查询参数</p>

<p>在不使用&nbsp;<code>URLSearchParams</code>&nbsp;我们通过正则的方式来完成获取查询参数的, 如下:</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">  <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getQueryString</span>(<span class="hljs-params">name</span>) </span>{</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">var</span> reg = <span class="hljs-keyword">new</span> <span class="hljs-built_in">RegExp</span>(<span class="hljs-string">"(^|&amp;)"</span> + name + <span class="hljs-string">"=([^&amp;]*)(&amp;|$)"</span>);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">var</span> r = <span class="hljs-built_in">window</span>.location.search.substr(<span class="hljs-number">1</span>).match(reg);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="5"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">return</span> r ? r[<span class="hljs-number">2</span>] : <span class="hljs-literal">null</span>;</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="6"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">  }</div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p>使用&nbsp;<code>URLSearchParams</code>&nbsp;之后:</p>

<pre class="has" name="code"><code class="language-javascript hljs"><ol class="hljs-ln"><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="1"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="2"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-comment">// 假设地址栏中查询参数是这样 "?post=1234&amp;action=edit"</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="3"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="4"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-keyword">var</span> urlParams = <span class="hljs-keyword">new</span> URLSearchParams(<span class="hljs-built_in">window</span>.location.search);</div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="5"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line"> </div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="6"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(urlParams.has(<span class="hljs-string">'post'</span>)); <span class="hljs-comment">// true</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="7"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(urlParams.get(<span class="hljs-string">'action'</span>)); <span class="hljs-comment">// "edit"</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="8"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(urlParams.getAll(<span class="hljs-string">'action'</span>)); <span class="hljs-comment">// ["edit"]</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="9"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(urlParams.toString()); <span class="hljs-comment">// "?post=1234&amp;action=edit"</span></div></div></li><li><div class="hljs-ln-numbers"><div class="hljs-ln-line hljs-ln-n" data-line-number="10"></div></div><div class="hljs-ln-code"><div class="hljs-ln-line">    <span class="hljs-built_in">console</span>.log(urlParams.append(<span class="hljs-string">'active'</span>, <span class="hljs-string">'1'</span>)); <span class="hljs-comment">// "?post=1234&amp;action=edit&amp;active=1"</span></div></div></li></ol></code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p>相比之前使用起来更加容易了.</p>
                                    </div>
                    </div>
    </article>
</div>


</details>

<b><details><summary>7. 详解bind,call和apply的区别</summary></b>

首先这三个方法都可以改变this的指向，下面从用法上来说一下他们的不同点

**一.bind**

    var name = 'sally';
     
    function sayName(){
        return this.name;
    }
    function sayName2(){
        return this.name
    }
     
    var o = {
        'name':'John',
        sayName:sayName,
        sayName2:sayName2.bind(window)
    };
    console.log(o.sayName()); //John
    console.log(o.sayName2());//sally  


结果看来很明显，两个方法都是o对象来调用的，在不使用bind改变this指向空间时，两个均为John,但由于bind的特殊作用,将其指向绑定为window的，因为最后一个输出了全局变量的name;

**二.call和apply**

相同点：call和apply均可以改变this指向，

不同点：call接受的参数为一个一个的，但是apply接受的参数只能为一个严格的数组(详情见如下的代码演示)


    var name = 'sally';
    function sayName(){
        return this.name;
    }
    var o = {
        'name':'John',
        sayName:sayName
    };
    console.log(sayName());
    
    结果为:sally    因为此时this所指对象为window

下面把代码改变一下

        var name = 'sally';
        function sayName(){
            return this.name;
        }
        var o = {
            'name':'John',
            sayName:sayName
        };
        
      console.log(sayName.call(o));
      console.log(sayName.apply(o));
      结果为:John 因为此时this所指对象为 o

下面看一下他们的不同点，上面也解释过，直接上代码看一下

      // call接收参数的形式
      
        var name = 'sally';
        function sayName(){
            console.log (this.name,arguments)
        }
        sayName.call(o,1,2,3);

      // apply接收参数的形式
      
        var name = 'sally';
        function sayName(){
            console.log (this.name,arguments)
        }
        sayName.apply(o,[1,2,3]);


</details>

<b><details><summary>8. js获取地址栏参数</summary></b>

**方法一：(基础版)**

    function getQueryString() {
      var sHref = window.location.href;
      var args = sHref.split("?");
      if (args[0] == sHref) {
        // 没有参数，直接返回空即可
        return "";
      }
      var arr = args[1].split("&");
      var obj = {};
      for (var i = 0; i < arr.length; i++) {
        var arg = arr[i].split("=");
        obj[arg[0]] = arg[1];
      }
      return obj;
    }
    var href = getQueryString();
    console.log(href["categoryId"]);

**方法二：(正则版,URL存在#则不适用)**

    function getQueryString(name) {
      var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
      var r = window.location.search.substr(1).match(reg);
      if (r != null) return unescape(r[2]);
      return null;
    }
    console.log(getQueryString('categoryId'))

**方法三：(正则升级版)**

    function getQueryString(name) {
      // 未传参，返回空
      if (!name) return null;
      // 查询参数：先通过search取值，如果取不到就通过hash来取
      var after = window.location.search;
      after = after.substr(1) || window.location.hash.split("?")[1];
      // 地址栏URL没有查询参数，返回空
      if (!after) return null;
      // 如果查询参数中没有"name"，返回空
      if (after.indexOf(name) === -1) return null;
      var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
      // 当地址栏参数存在中文时，需要解码，不然会乱码
      var r = decodeURI(after).match(reg);
      // 如果url中"name"没有值，返回空
      if (!r) return null;
      return r[2];
    }
    console.log(getQueryString('categoryId'))


</details>

<b><details><summary>9. 跨域问题的解决方法</summary></b>

## 一、什么是跨域？

在前端领域中，跨域是指浏览器允许向服务器发送跨域请求，从而克服Ajax只能同源使用的限制

**什么是同源策略？**

同源策略是一种约定，由Netscape公司1995年引入浏览器，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，浏览器很容易受到XSS、CSFR等攻击。所谓同源是指"协议+域名+端口"三者相同，即便两个不同的域名指向同一个ip地址，也非同源。

**同源策略限制以下几种行为：**

- Cookie、LocalStorage 和 IndexDB 无法读取
- DOM和JS对象无法获得
- AJAX 请求不能发送

## 二、常见的跨域场景

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717143750217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0Ffc291bG1hdGU=,size_16,color_FFFFFF,t_70)

## 三、9种跨域解决方案

**1、JSONP跨域**

jsonp的原理就是利用`<script>`标签没有跨域限制，通过`<script>`标签src属性，发送带有callback参数的GET请求，服务端将接口返回数据拼凑到callback函数中，返回给浏览器，浏览器解析执行，从而前端拿到callback函数返回的数据。
1）原生JS实现：



    <script>
        var script = document.createElement('script');
        script.type = 'text/javascript';
    
        // 传参一个回调函数名给后端，方便后端返回时执行这个在前端定义的回调函数
        script.src = 'http://www.domain2.com:8080/login?user=admin&callback=handleCallback';
        document.head.appendChild(script);
    
        // 回调执行函数
        function handleCallback(res) {
            alert(JSON.stringify(res));
        }
     </script>

服务端返回如下（返回时即执行全局函数）：

    handleCallback({"success": true, "user": "admin"})

2）jquery Ajax实现：

    $.ajax({
        url: 'http://www.domain2.com:8080/login',
        type: 'get',
        dataType: 'jsonp',  // 请求方式为jsonp
        jsonpCallback: "handleCallback",  // 自定义回调函数名
        data: {}
    });

3）Vue axios实现：

    this.$http = axios;
    this.$http.jsonp('http://www.domain2.com:8080/login', {
        params: {},
        jsonp: 'handleCallback'
    }).then((res) => {
        console.log(res); 
    })

**2、跨域资源共享（CORS）**

CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。
它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源使用的限制。
CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。
浏览器将CORS跨域请求分为简单请求和非简单请求。
只要同时满足一下两个条件，就属于简单请求
(1)使用下列方法之一：

- head
- get
- post

(2)请求的Heder是

- Accept
- Accept-Language
- Content-Language
- Content-Type: 只限于三个值：*application/x-www-form-urlencoded、multipart/form-data、text/plain*

不同时满足上面的两个条件，就属于非简单请求。浏览器对这两种的处理，是不一样的。

**简单请求**
对于简单请求，浏览器直接发出CORS请求。具体来说，就是在头信息之中，增加一个Origin字段。

    GET /cors HTTP/1.1
    Origin: http://api.bob.com
    Host: api.alice.com
    Accept-Language: en-US
    Connection: keep-alive
    User-Agent: Mozilla/5.0...

上面的头信息中，Origin字段用来说明，本次请求来自哪个源（协议 + 域名 + 端口）。服务器根据这个值，决定是否同意这次请求。

**CORS请求设置的响应头字段，都以 Access-Control-开头:**

**1）Access-Control-Allow-Origin：必选**

它的值要么是请求时Origin字段的值，要么是一个*，表示接受任意域名的请求。
**2）Access-Control-Allow-Credentials：可选**

它的值是一个布尔值，表示是否允许发送Cookie。默认情况下，Cookie不包括在CORS请求之中。设为true，即表示服务器明确许可，Cookie可以包含在请求中，一起发给服务器。这个值也只能设为true，如果服务器不要浏览器发送Cookie，删除该字段即可。
**3）Access-Control-Expose-Headers：可选**

CORS请求时，XMLHttpRequest对象的getResponseHeader()方法只能拿到6个基本字段：Cache-Control、Content-Language、Content-Type、Expires、Last-Modified、Pragma。如果想拿到其他字段，就必须在Access-Control-Expose-Headers里面指定。上面的例子指定，getResponseHeader('FooBar')可以返回FooBar字段的值。

**非简单请求**

非简单请求是那种对服务器有特殊要求的请求，比如请求方法是PUT或DELETE，或者Content-Type字段的类型是application/json。非简单请求的CORS请求，会在正式通信之前，增加一次HTTP查询请求，称为"预检"请求（preflight）。

**预检请求**

预检"请求用的请求方法是OPTIONS，表示这个请求是用来询问的。请求头信息里面，关键字段是Origin，表示请求来自哪个源。除了Origin字段，"预检"请求的头信息包括两个特殊字段。

    OPTIONS /cors HTTP/1.1
    Origin: http://api.bob.com
    Access-Control-Request-Method: PUT
    Access-Control-Request-Headers: X-Custom-Header
    Host: api.alice.com
    Accept-Language: en-US
    Connection: keep-alive
    User-Agent: Mozilla/5.0..

**1）Access-Control-Request-Method：必选**

用来列出浏览器的CORS请求会用到哪些HTTP方法，上例是PUT。
**2）Access-Control-Request-Headers：可选**

该字段是一个逗号分隔的字符串，指定浏览器CORS请求会额外发送的头信息字段，上例是X-Custom-Header。

**预检请求的回应**

服务器收到"预检"请求以后，检查了Origin、Access-Control-Request-Method和Access-Control-Request-Headers字段以后，确认允许跨源请求，就可以做出回应。
HTTP回应中，除了关键的是Access-Control-Allow-Origin字段，其他CORS相关字段如下：

**1）Access-Control-Allow-Methods：必选**

它的值是逗号分隔的一个字符串，表明服务器支持的所有跨域请求的方法。注意，返回的是所有支持的方法，而不单是浏览器请求的那个方法。这是为了避免多次"预检"请求。

**2）Access-Control-Allow-Headers**

如果浏览器请求包括Access-Control-Request-Headers字段，则Access-Control-Allow-Headers字段是必需的。它也是一个逗号分隔的字符串，表明服务器支持的所有头信息字段，不限于浏览器在"预检"中请求的字段。

**3）Access-Control-Allow-Credentials：可选**

该字段与简单请求时的含义相同。

**4）Access-Control-Max-Age：可选**

用来指定本次预检请求的有效期，单位为秒。

**CORS跨域示例**


**1）前端设置：**

- 原生js：

      var xhr = new XMLHttpRequest(); // IE8/9需用window.XDomainRequest兼容
      
      // 前端设置是否带cookie
      xhr.withCredentials = true;
      
      xhr.open('post', 'http://www.domain2.com:8080/login', true);
      xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
      xhr.send('user=admin');
      
      xhr.onreadystatechange = function() {
          if (xhr.readyState == 4 && xhr.status == 200) {
              alert(xhr.responseText);
          }
      };
- 前端jQuery写法：

  	$.ajax({
  		    type: "POST",
  		    url: baseUrl + "/post",
  		    dataType: 'json',
  		    //  开启跨域
  		    crossDomain: true,
  		    xhrFields: {
  		        withCredentials: true
  		    },
  		    data: {
  		        name: "name_from_frontend"
  		    },
  		    success: function (response) {
  		        console.log(response)// 返回的 json 数据
  		        $("#response").val(JSON.stringify(response));
  		    }
  		});

**2）服务端设置：**

- nodejs代码

      var http = require('http');
      var server = http.createServer();
      var qs = require('querystring');
      server.on('request', function(req, res) {
     

        var postData = '';
   	
   	    // 数据块接收中
   	    req.addListener('data', function(chunk) {
   	        postData += chunk;
   	    });
   	
   	    // 数据接收完毕
   	    req.addListener('end', function() {
   	        postData = qs.parse(postData);
   	
   	        // 跨域后台设置
   	        res.writeHead(200, {
   	            'Access-Control-Allow-Credentials': 'true',     // 后端允许发送Cookie
   	            'Access-Control-Allow-Origin': 'http://www.domain1.com',    // 允许访问的域（协议+域名+端口）
   	            /* 
   	             * 此处设置的cookie还是domain2的而非domain1，因为后端也不能跨域写cookie(nginx反向代理可以实现)，
   	             * 但只要domain2中写入一次cookie认证，后面的跨域接口都能从domain2中获取cookie，从而实现所有的接口都能跨域访问
   	             */
   	            'Set-Cookie': 'l=a123456;Path=/;Domain=www.domain2.com;HttpOnly'  // HttpOnly的作用是让js无法读取cookie
   	        });
   	
   	        res.write(JSON.stringify(postData));
   	        res.end();
   	    });
   	});
        server.listen('8080');
        console.log('Server is running at port 8080...');

- java代码

           // 这是spring4.2以上版本
           
  	   @Configuration
      	public class WebConfig extends WebMvcConfigurerAdapter {
  	 
  	    @Override
  	    public void addCorsMappings(CorsRegistry registry) {
  	        registry.addMapping("/**/*").allowedOrigins("*");
  	    }
  	   }
  	   
        //  4.2以下的：
        
  	public class CrossDomainFilter extends OncePerRequestFilter {
  	    @Override
  	    protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain filterChain) throws ServletException, IOException {
  	        response.addHeader("Access-Control-Allow-Origin", "*");// 如果提示 * 不行，请往下看
  	        response.addHeader("Access-Control-Allow-Credentials", "true");
  	        response.addHeader("Access-Control-Allow-Methods", "GET, POST, PUT, DELETE");
  	        response.addHeader("Access-Control-Allow-Headers", "Content-Type");
  	        filterChain.doFilter(request, response);
  	    }
  	}

             //  需要加过滤器
             
  		<filter>
  		    <filter-name>CrossDomainFilter</filter-name>
  		    <filter-class>com.javadoop.filters.CrossDomainFilter</filter-class>
  		</filter>
  		<filter-mapping>
  		    <filter-name>CrossDomainFilter</filter-name>
  		    <url-pattern>/*</url-pattern>
  		</filter-mapping>

**3、nginx代理跨域**

nginx代理跨域，实质和CORS跨域原理一样，通过配置文件设置请求响应头Access-Control-Allow-Origin...等字段。

**1）nginx配置解决iconfont跨域**

浏览器跨域访问js、css、img等常规静态资源被同源策略许可，但iconfont字体文件(eot|otf|ttf|woff|svg)例外，此时可在nginx的静态资源服务器中加入以下配置。

    location / {
      add_header Access-Control-Allow-Origin *;
    }

**2）nginx反向代理接口跨域**

实现思路：通过Nginx配置一个代理服务器域名与domain1相同，端口不同）做跳板机，反向代理访问domain2接口，并且可以顺便修改cookie中domain信息，方便当前域cookie写入，实现跨域访问。
nginx具体配置：

    #proxy服务器
    server {
        listen       81;
        server_name  www.domain1.com;
        location / {
            proxy_pass   http://www.domain2.com:8080;  #反向代理
            proxy_cookie_domain www.domain2.com www.domain1.com; #修改cookie里域名
            index  index.html index.htm;
            # 当用webpack-dev-server等中间件代理接口访问nignx时，此时无浏览器参与，故没有同源限制，下面的跨域配置可不启用
            add_header Access-Control-Allow-Origin http://www.domain1.com;  #当前端只跨域不带cookie时，可为*
            add_header Access-Control-Allow-Credentials true;
        }
    }

**4、vue框架的跨域**

node + vue + webpack + webpack-dev-server搭建的项目，跨域请求接口，直接修改webpack.config.js配置。开发环境下，vue渲染服务和接口代理服务都是webpack-dev-server同一个，所以页面与代理接口之间不再跨域。
webpack.config.js部分配置：


    module.exports = {
        entry: {},
        module: {},
        ...
        devServer: {
            historyApiFallback: true,
            proxy: [{
                context: '/login',
                target: 'http://www.domain2.com:8080',  // 代理跨域目标接口
                changeOrigin: true,
                secure: false,  // 当代理某些https服务报错时用
                cookieDomainRewrite: 'www.domain1.com'  // 可以为false，表示不修改
            }],
            noInfo: true
        }
    }

**5、WebSocket协议跨域**

WebSocket protocol是HTML5一种新的协议。它实现了浏览器与服务器全双工通信，同时允许跨域通讯，是server push技术的一种很好的实现。
原生WebSocket API使用起来不太方便，我们使用Socket.io，它很好地封装了webSocket接口，提供了更简单、灵活的接口，也对不支持webSocket的浏览器提供了向下兼容。

1）前端代码：

    <div>user input：<input type="text"></div>
    <script src="https://cdn.bootcss.com/socket.io/2.2.0/socket.io.js"></script>
    <script>
    var socket = io('http://www.domain2.com:8080');
    
    // 连接成功处理
    socket.on('connect', function() {
        // 监听服务端消息
        socket.on('message', function(msg) {
            console.log('data from server: ---> ' + msg); 
        });
    
        // 监听服务端关闭
        socket.on('disconnect', function() { 
            console.log('Server socket has closed.'); 
        });
    });
    
    document.getElementsByTagName('input')[0].onblur = function() {
        socket.send(this.value);
    };
    </script>

2）Nodejs socket后台：


    var http = require('http');
    var socket = require('socket.io');
    
    // 启http服务
    var server = http.createServer(function(req, res) {
        res.writeHead(200, {
            'Content-type': 'text/html'
        });
        res.end();
    });
    
    server.listen('8080');
    console.log('Server is running at port 8080...');
    
    // 监听socket连接
    socket.listen(server).on('connection', function(client) {
        // 接收信息
        client.on('message', function(msg) {
            client.send('hello：' + msg);
            console.log('data from client: ---> ' + msg);
        });
    
        // 断开处理
        client.on('disconnect', function() {
            console.log('Client socket has closed.'); 
        });
    });


</details>

<b><details><summary>10. var与let、const的区别</summary></b>

**一、var声明的变量会挂载在window上，而let和const声明的变量不会：**

    var a = 100;
    console.log(a,window.a);    // 100 100
    
    let b = 10;
    console.log(b,window.b);    // 10 undefined
    
    const c = 1;
    console.log(c,window.c);    // 1 undefined
**二、var声明变量存在变量提升，let和const不存在变量提升**

    console.log(a); // undefined  ===>  a已声明还没赋值，默认得到undefined值
    var a = 100;
    
    console.log(b); // 报错：b is not defined  ===> 找不到b这个变量
    let b = 10;

    console.log(c); // 报错：c is not defined  ===> 找不到c这个变量
    const c = 10;

**三、let和const声明形成块作用域**

    if(1){
        var a = 100;
        let b = 10;
    }
    
    console.log(a); // 100
    console.log(b)  // 报错：b is not defined  ===> 找不到b这个变量


    if(1){
    
        var a = 100;
            
        const c = 1;
    }
     console.log(a); // 100
     console.log(c)  // 报错：c is not defined  ===> 找不到c这个变量

**四、同一作用域下let和const不能声明同名变量，而var可以**

    var a = 100;
    console.log(a); // 100
    
    var a = 10;
    console.log(a); // 10

    let a = 100;
    let a = 10;
    
    //  控制台报错：Identifier 'a' has already been declared  ===> 标识符a已经被声明了。

**五、暂存死区**

    var a = 100;
    
    if(1){
        a = 10;
        //在当前块作用域中存在a使用let/const声明的情况下，给a赋值10时，只会在当前作用域找变量a，
        // 而这时，还未到声明时候，所以控制台Error:a is not defined
        let a = 1;
    }

**六、const**

    /*
    * 　　1、一旦声明必须赋值,不能使用null占位。
    *
    * 　　2、声明后不能再修改
    *
    * 　　3、如果声明的是复合类型数据，可以修改其属性
    *
    * */
    
    const a = 100; 
    
    const list = [];
    list[0] = 10;
    console.log(list);　　// [10]
    
    const obj = {a:100};
    obj.name = 'apple';
    obj.a = 10000;
    console.log(obj);　　// {a:10000,name:'apple'}



</details>

<b><details><summary>11. 正则表达式总结</summary></b>

**1.数字/货币金额（支持负数、千分位分隔符）**

    /(^[-]?[1-9]\d{0,2}($|(,\d{3})*($|(\.\d{1,2}$))))|((^[0](\.\d{1,2})?)|(^[-][0]\.\d{1,2}))$/

**2.数字/货币金额 (只支持正数、不支持校验千分位分隔符)**

    /(^[1-9]([0-9]+)?(\.[0-9]{1,2})?$)|(^(0){1}$)|(^[0-9]\.[0-9]([0-9])?$)/
**3.银行卡号（16或19位）**

    /^([1-9]{1})(\d{15}|\d{18})$/
**4.中文姓名**

    /^([\u4e00-\u9fa5·]{2,10})$/
**5.手机号(严谨), 根据工信部2019年最新公布的手机号段**

    /^1((3[\d])|(4[5,6,7,9])|(5[0-3,5-9])|(6[5-7])|(7[0-8])|(8[\d])|(9[1,8,9]))\d{8}$/

**6.手机号(宽松), 只要是13,14,15,16,17,18,19开头即可**

    /^1[3-9]\d{9}$/
**7.email地址**

    /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/
**8.国内座机电话,如: 0341-86091234**

    /\d{3}-\d{8}|\d{4}-\d{7}/
**9.二代身份证号(18位数字),最后一位是校验位,可能为数字或字符X**

    /^\d{6}(18|19|20)\d{2}(0\d|11|12)([0-2]\d|30|31)\d{3}(\d|X|x)$/


</details>
