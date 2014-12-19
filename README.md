#log4web
##简介
基于浏览器端的console的日志记录组件。支持如下特性：
1.日志级别设置；
2.异常提交到服务器；
3.提交环境信息；
4.日志Tag过滤器；

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


####调用示例：
```js


```
##API说明


##测试用例

##浏览器兼容性
兼容IE8+,chrome,firefox。
##依赖
不需要依赖其他库。
##协议
采用[MIT 许可协议](https://github.com/houyhea/timespanjs/blob/master/LICENSE)。
##帮助
支付宝赞助（houyhea）：  
![赞助](https://raw.githubusercontent.com/houyhea/lab/master/alipayqrcode.png)