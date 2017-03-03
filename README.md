# seblePrinter
<p style="color: #ccc; margin-bottom: 30px;">

<div class="outline">
[init](#a1)

[connect](#a2)

[print](#a3)

[printLocal](#a4)
</div>

#**概述**

**微信简介**

**seblePrinter 模块概述**

本模块封装了蓝牙小票打印机，通过html网页形式打印小票，使用起来方便，可自定义格式和内容。

## [实例widget下载地址](https://github.com/XM-Right/wx-Example/archive/master.zip)
    
##**模块接口**
    
<div id="a1"></div>
#**init**

搜索小票打印机蓝牙接口

isInstalled(callback(ret, err))

##init(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    perpherals: []     //数组类型；数组内包含字典，属性分别为id（数字类型）、name（字符串类型）、state（数字类型，0为没有连接，1为正在连接，2为已经连接，3为正在连接）

}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
    error: 0        //数字类型；
                    //错误码：
                    //0（未知错误），
                    //1（正在重启），
                    //2（设备不支持），
                    //3（未授权），
                    //4（蓝牙可用，但是未打开），
                    //5（搜索超时）
}
```
##示例代码

```js
var printer = api.require('seblePrinter');
printer.init(function(ret, err){
    alert(JSON.stringify(ret));
});

```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**connect**

连接小票打印机接口

connect({params}, callback(ret, err))

##params

id：

- 类型：数字类型
- 描述：默认值为0，填写init接口返回的id。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    message: "连接成功"   //字符串；连接成功描述信息
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
  message: "连接失败"   //字符串；连接失败描述信息
}
```

##示例代码

```js
var printer = api.require('seblePrinter');
printer.connect({
    id : 0
},function(ret,err){
    alert(JSON.stringify(ret));
});

```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**print**

打印小票接口

print({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 描述：打印小票的html网络地址。

alignment：

- 类型：数字类型
- 描述：对齐方式
- 默认值：0
- 取值范围：
    * 0（居中）
    * 1（左对齐）
    * 2（右对齐）

maxWidth：

- 类型：数字类型
- 描述：最大宽度
- 默认值：450

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    state: 0    //数字类型；0为成功，1为失败
    message:""  //字符串；描述信息
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
            //无返回值
}
```

##示例代码

```js
var printer = api.require('seblePrinter');
printer.print({
    url:''
},function(ret,err){
    alert(JSON.stringify(ret));
});

```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**printLocal**

打印小票本地测试接口

print({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：打印小票的html本地地址（格式为 widget://）。

alignment：

- 类型：数字类型
- 描述：对齐方式
- 默认值：0
- 取值范围：
* 0（居中）
* 1（左对齐）
* 2（右对齐）

maxWidth：

- 类型：数字类型
- 描述：最大宽度
- 默认值：450

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
state: 0    //数字类型；0为成功，1为失败
message:""  //字符串；描述信息
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
            //无返回值
}
```

##示例代码

```js
var printer = api.require('seblePrinter');
printer.printLocal({
    path:'widget://res/print.html'
},function(ret,err){
    alert(JSON.stringify(ret));
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本
