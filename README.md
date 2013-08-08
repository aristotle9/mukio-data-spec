mukio-data-spec
===============

Message format specification between *MukioPlayer* Client and Server

## Target

*mukio-data-spec* 并非是一个程序项目, 而是提供一个用于 *MukioPlayer* 播放器与服务器交换数据的规范.

***MukioPlayer* Client, *MukioPlayer* 播放器**

一个基于 flash 的弹幕视频播放器.
项目地址: <http://code.google.com/p/mukioplayer/>

***MukioPlayer* Server, *MukioPlayer* 服务器**

*MukioPlayer* 播放器的弹幕数据后端. 为播放器提供弹幕数据的存取与实时订阅服务. 包括基于 REST 的 HTTP 服务器和基于 RPC 的 socket/websocket 消息发布服务器.

项目由以下几个部分组成:

1. [弹幕数据](https://github.com/aristotle9/mukio-data-spec/blob/master/basic.md)
2. HTTP 弹幕存取
3. 基于文本的实时 RPC 协议
4. 服务器示例程序

本项目描述的规范的客户端部分, 将在 *MukioPlayer* 播放器未来的版本中实现. 


