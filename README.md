#log4web
##简介
基于浏览器端的console的日志记录组件。支持如下特性：

1. 日志级别设置；
2. 异常提交到服务器；
3. 提交环境信息；
4. 日志Tag过滤器；

###如何使用


####浏览器下的引用
```js
<script src="log4web.js"></script>
<script>
    log4web.log("houyhea");
    log4web.error(new Error("houyhea"));
</script>
```
####requirejs下的引用
```js
require.config({
    paths: {
        "log4web": "path/to/log4web",
    }
});
define(["log4web"], function (log4web) {
    log4ewb.log("houyhea");
    log4web.error(new Error("houyhea"));
});
```

##API说明
###config(config)
对日志组件进行配置。如果不传参数，则返回当前日志组件的配置信息。
配置项主要有：

####debug
是否开启调试模式。如果开启调试模式，则可以在console中输入window.log4web进行调试.默认值：0.
####level
日志级别，error(4)、warn(3)、info(2)、log(1)、debug(0),级别越高，输出的日志越少。比如：当前级别如果是warn，则只输出error、warn的日志.默认值：debug;
代码示例
```js
var Level = {
        "error": 4,
        "warn": 3,
        "info": 2,
        "log": 1,
        "debug": 0
    };
```

####tagFilter
日志tag筛选,正则表达式字符串.使用者可以通过在console控制台通过**log4web.config({tagFilter:"usersmodule"})**配置值输出"usersmodule"tag的日志。默认值："".
```js
log4web.config({tagFilter:"usersmodule"});
```
####post
当发生异常是是否post到服务器。**此处只有当msg参数是Error对象时，才判断是否有提交到服务器**.默认值：0.
####postContextInfo
是否提交环境数据.默认值：1
####postUrl
异常信息提交的服务器地址.默认值："/api/exception"。
代码示例：
```js
log4web.config({
            debug: 0,
            level: "debug",
            tagFilter: "",
            post: 0,
            postContextInfo: 1,
            postUrl: "/api/exception"
        });
```
这里单独说一下postData，主要包含如下信息：

1. browser.浏览器描述信息。返回字符串，格式：" Chrome,39.0.2171.95",逗号前表示浏览器类型，逗号后表示浏览器版号.
2. os.操作系统字符串。
3. flash.返回字符串，格式："1,15",逗号分隔，第一个表示是否安装flash，1：是，0：否。15:表示flash版本.
4. referrer.document.referrer信息.
5. url.当前页面的url.
6. resolution.屏幕分辨率信息.返回格式："1920*1080",(window.screen对象获取）.
7. name.异常名称。
8. message.异常message。
9. stack.异常调用堆栈字符串。

###log(msg,tag)
####msg
日志消息。可以是字符串或Error对象。
####tag
用于过滤器，可为空。
调用示例：
```js
log4web.log("log info.","usersmodule");
log4web.log("log info.");
```
###info(msg,tag)
####msg
日志消息。可以是字符串或Error对象。
####tag
用于过滤器，可为空。
###debug(msg,tag)
####msg
日志消息。可以是字符串或Error对象。
####tag
用于过滤器，可为空。
###warn(msg,tag)
####msg
日志消息。可以是字符串或Error对象。
####tag
用于过滤器，可为空。
###error(msg,tag)
####msg
日志消息。可以是字符串或Error对象。
####tag
用于过滤器，可为空。


##测试用例
[参见](https://github.com/houyhea/log4web/blob/master/test/unitTest.html)。
##浏览器兼容性
兼容IE8+,chrome,firefox。
##依赖
需要依赖**jquery**库，post数据用到了jquery.post方法。如果不想依赖jquery，可自行修改相关代码。
##协议
采用[MIT 许可协议](https://github.com/houyhea/log4web/blob/master/LICENSE)。
##帮助
支付宝赞助（houyhea）：  
![赞助](https://raw.githubusercontent.com/houyhea/lab/master/alipayqrcode.png)