## 1.http的架构模式
### http是客户端/服务器模式中请求-响应所用的协议，在这种模式中，客户端（一般是web浏览器）向服务器提交http请求，服务器响应请求的资源
### http的特点
-  http是半双工协议，也就是说，在同一时刻数据只能单向流动，客户端向服务器发送请求（单向的），然后服务器响应请求（单向的）。
- 服务器不能主动推送数据给浏览器。
## 2.双向通信
comet是一种用于web的推送技术，能使用服务器能实时的将更新的信息传送到客户端，而无需客户端发出请求，目前有三种实现方式：轮询、长轮询和iframe流
### 1.轮询
- 轮询是客户端和服务器之间会一直进行连接，每隔一段时间就询问一次
- 这种范式连接数会很多，一个接受，一个发送。而且每次发送请求都会有http的header，会很耗流量，也会消耗cpu的利用率。
### 2.长轮询
- 长轮询是对轮询的改进版，客户端发送http给服务器之后，看有没有新消息，如果没有新消息，就一直等待。
- 当有新消息的时候，才会返回给客户端。在某种程度上减小了网络带宽和cup利用率等问题。
- 由于http数据包的头部数据量往往很大（通常有400多个字节），但是真正被服务器需要的数据却很少（有的只有10个字节左右），这样的数据包在网络上周期性的传输，难免对网络带宽是一种浪费。
### iframe流
- 通过在html页面里嵌入一个隐藏的iframe，然后将这个iframe的src属性设为对一个长连接的请求，服务器端就能源源不断地向客户端推送数据。
