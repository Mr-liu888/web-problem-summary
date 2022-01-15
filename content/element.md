# [返回主页](https://github.com/Mr-liu888/web-problem-summary/blob/main/README.md)

<b><details><summary>1. Upload组件上传时如何携带参数</summary></b>

今天在写文件上传时,想要在上传的时候携带参数。于是查阅element官网寻找答案，经过一番搜索，终于解决了此问题，现在分享给大家。

**可以直接使用 :data={参数} ,参数为键值对的形式{key1:value1,key2:value2},传递参数,如下**

```javascript
<el-upload
	class="avatar-uploader"
	action="/setmeal/updatePicture.do"
	:data={pictureName:this.imageName}
	:auto-upload="autoUpload"
	name="imgFile"
	:show-file-list="false"
	:on-success="handleAvatarSuccess"
	:before-upload="beforeAvatarUpload">
</el-upload>
```
这样就可以在上传文件,访问后端时携带参数

![在这里插入图片描述](https://img-blog.csdnimg.cn/7d4a0466d56c46adb1364f391546f221.png)

</details>

<b><details><summary>2. table表格多选状态如何禁选?</summary></b>

对elementUI中table表格的多选框进行 可勾选 和 不可勾选 的处理给 type 属性为 selection 的加一个事件:selectable='selected’

```javascript
<el-table-column type="selection" width="55" :selectable="selected"> </el-table-column>

methods中：判断后台给返回的状态码

selected(row, index) {
	if (row.WaitConfirmRecord.is_confirm == 1) {
		return false //不可勾选
	} else {
		return true; //可勾选
	}
},
```

效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/6834c36daeaf42d6bc955baeb6937fbf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA54ix54Sw,size_18,color_FFFFFF,t_70,g_se,x_16)

</details>

<b><details><summary>3. el-table中的label换行问题</summary></b>

想要实现label中换行的问题，我们以下面两种方式进行解决。

**1.依赖CSS的方法**

```javascript
1.label中增加 \n
<el-table-column prop="name" :label="'姓名\nname'" min-width="100"></el-table-column>

2.设置white-space样式
.el-table .cell {
　　white-space: pre-line;
}
如果没有生效，查看一下css的权重问题，粗暴的方法可以使用!important
```
**2.label中增加/，绑定render-header方法**

```javascript
<el-table-column :render-header="renderHeader" prop="capacity" label="姓名/name" min-width="90" align="center" />

renderHeader方法:

renderHeader(h, { column }) {
   return h('span', {}, [
     h('span', {}, column.label.split('/')[0]),
     h('br'),
     h('span', {}, column.label.split('/')[1])
   ])
 }
```
**3.效果**

![在这里插入图片描述](https://img-blog.csdnimg.cn/7aebe82308e84ef9a7ef6b4b66373a09.png)
</details>

<b><details><summary>4. datepicker日期选择器时间选择范围限制</summary></b>

1.单个输入框的情况

```javascript
<el-date-picker
       v-model="value1"
       type="date"
       placeholder="选择日期"
       :picker-options="pickerOptions0">
</el-date-picker>
```
情景1: 设置选择今天以及今天之后的日期

```javascript
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() < Date.now() - 8.64e7;
          }
        }, 
   }    
}
```
情景2: 设置选择今天以及今天以前的日期

```javascript
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() > Date.now() - 8.64e6
          }
        }, 
   }    
}
```
情景3: 设置选择今天之后的日期（不能选择当天时间）

```javascript
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() < Date.now();
          }
        },  
   }     
}
```
情景4: 设置选择今天之前的日期（不能选择当天）

```javascript
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() > Date.now();
          }
        },  
   }     
}
```
情景5: 设置选择三个月之前到今天的日期

```javascript
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            let curDate = (new Date()).getTime();
            let three = 90 * 24 * 3600 * 1000;
            let threeMonths = curDate - three;
            return time.getTime() > Date.now() || time.getTime() < threeMonths;;
          }
        }, 
   }    
}
```
2.两个输入框的情况

```javascript
<el-date-picker
       v-model="value1"
       type="date"
       placeholder="开始日期"
       :picker-options="pickerOptions0">
</el-date-picker>
<el-date-picker
       v-model="value2"
       type="date"
       placeholder="结束日期"
       :picker-options="pickerOptions1">
</el-date-picker>
```
情景1: 限制结束日期不能大于开始日期

```javascript
data(){
    return {
         pickerOptions0: {
                disabledDate: (time) => {
                    if (this.value2 != "") {
                        return time.getTime() > Date.now() || time.getTime() > this.value2;
                    } else {
                        return time.getTime() > Date.now();
                    }
 
                }
            },
            pickerOptions1: {
                disabledDate: (time) => {
                    return time.getTime() < this.value1 || time.getTime() > Date.now();
                }
            },
    }     
}
```

</details>

