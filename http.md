## HTTP弹幕存取接口

### 客户端的`cid`

*MukioPlayer* 播放器对弹幕的存取都必须在 `cid` 上下文中。`cid` 通过 flash 嵌入代码的 [`flashvars`](http://helpx.adobe.com/flash/kb/pass-variables-swfs-flashvars.html) 属性传递给客户端，`cid` 即键名。

客户端总是将 `cid` 当作 **String 类型**处理，这主要体现在编码 JSON 时。

### 存取弹幕的 HTTP 接口地址

通过修改 *MukioPlayer* 播放器同一路径下的 `conf.xml` 文件，来配置存取弹幕的 HTTP 接口地址。

相关配置片段：

```
<?xml version="1.0" encoding="utf-8"?>
<conf>
  <performance>
    ...
  </performance>
  <server>
	...
    <!-- 弹幕加载地址,变量{$cid}为弹幕cid -->
    <load>/path_for_load?cid={$cid}</load>
    <!-- 弹幕发送地址,变量{$cid}为弹幕cid -->
    <send>/path_for_send</send>
	...
  </server>
</conf>
```

存取弹幕的 HTTP 地址中，可能需要包含弹幕的 `cid`，这也可以在配置文件中实现。

配置中的地址变量会在下面的文档中，以 . 分隔的路径加以引用。

### 弹幕存储（发送）

Location: conf.server.send

Method: POST

Body: JSON-encoded

```
{
  text:
  stime:
  color:
  mode:
  size:
  cid: String, passed through flashvars
  postdate: UNIX timestamp in milliseconds
  context: Integer, should be returned within response
}
```

Return: JSON-encoded

```
{
  context: Integer, same as the context property in post body
  id: Danmu id, if accepted by server, or should not be provided
  error: The reason when rejected by server, otherwise should not be provided
    {
      code: Error code, defined by Server
      message: Error information to display to user
    }
}
```

### 弹幕获取

Location: conf.server.load

Method: GET

Params: `cid` will be passed by `{$cid}` interpolation in *Location*

Return: JSON-encoded

```
{
  cid:
  data: Array of Danmu data objects
}
```