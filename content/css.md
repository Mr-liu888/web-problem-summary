# [返回主页](https://github.com/Mr-liu888/web-problem-summary/blob/main/README.md)

<b><details><summary>1. 实现必填项前添加红色星号</summary></b>

在前端实现表单验证的过程中，有些必填项需要加星号提醒，怎样实现呢，下面介绍两种方法实现。
1 . 常规写法

```javascript
<label><span style="color:red;">* </span>爱焰 : </label>
<input type="text" value=""/>
```
2 . CSS写法(更简洁方便 , 而且便于统一调整样式)

```javascript
<style>
    label.xrequired:before {
        content: '* ';
        color: red;
    }
</style>
<label class="xrequired">爱焰 : </label>
<input type="text" value=""/>
```


</details>

<b><details><summary>2. css各种浏览器兼容写法</summary></b>

```javascript
  * ， ie6,ie7可以识别；

  _和- ，  ie6可以识别；

  !important  ,表示高优先级，ie7及以上，firefox都支持，ie6认识带!important的样式属性，但不认识!important的优先级；
    
  -webkit- ，针对safari，chrome浏览器的内核CSS写法
    
  -moz-，针对firefox浏览器的内核CSS写法
    
  -ms-，针对ie内核的CSS写法
    
  -o-，针对Opera内核的CSS写法
```

可以根据不同的浏览器写css hack 来达到兼容不同的浏览器，亲测有效！
</details>

