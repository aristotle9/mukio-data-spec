## HTTP弹幕存取接口

### 客户端的`cid`

*MukioPlayer* 播放器对弹幕的存取都必须在 `cid` 上下文中。`cid` 通过 flash 嵌入代码的 [`flashvars`](http://helpx.adobe.com/flash/kb/pass-variables-swfs-flashvars.html) 属性传递给客户端，`cid` 即键名。

客户端总是将 `cid` 当作 **String 类型**处理，这主要体现在编码 JSON 时。

### 存取 URL 位置配置



### 弹幕存储(发送)


### 弹幕获取