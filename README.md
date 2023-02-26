# resouces

pacproxy compiled executable programes and manuals

pac加密代理服务器，编译好的绿色可执行程序和说明文档

服务器软件在[pacproxy-server文件夹](pacproxy-server)

客户端软件wssagent在[wssproxy-agent文件夹](wssproxy-agent)


## pacproxy 服务器设置（参数示例）：

```
  paclink: '/pacurl_direct',

  iphours: 2,
  
  pacpass: [ '/pacurl_need_password', 'proxy_user', 'proxy_pass' ],
  
  domain: 'your.proxy.com',
```
服务器说明详见：https://github.com/httpgate/pacproxy-server


## 用pacurl翻墙：

运行服务器后，服务器会显示以下pacurl:

pacurl1 :  https://your.proxy.com/pacurl_direct

pacurl2 (浏览器会提示输入用户密码）： https://your.proxy.com/pacurl_need_password

   用户/密码：proxy_user / proxy_pass


可以直接将pacurl设置在Firefox浏览器内，或wifi网络设置上

pacurl翻墙说明详见： https://github.com/httpgate/pacproxy.js/blob/main/documents/DeviceSetting_ZH.md

Firefox设置：

![Firefox设置图](Firefox.JPG)


## 用websocket url (简称wssurl)翻墙：

运行服务器后，服务器还会显示以下wssurl:

直连websocket url1:  wss://your.proxy.com/pacurl_direct   （用于全局代理，可让聊天软件等翻墙)

直连websocket url2:  wss://your.proxy.com/pacurl_direct/tls  （用于域名伪装时的tls验证)


需要在命令行运行wssagent软件，示例： ./wssagent-linux  wss://your.proxy.com/pacurl_direct/tls  3128

翻墙说明详见：https://github.com/httpgate/wssproxy-agent

Firefox设置见上图，选中Manual proxy configuration


## 用支持websocket的CDN中转翻墙

可以在类似cloudflare的支持websocket的CDN创建一个域名，如cdn.proxy.com，并将域名指向代理服务器的IP地址

CDN中转 websocke url1:   wss://cdn.proxy.com/pacurl_direct   （CDN能知道部分传输内容）

CDN中转 websocke url2:   wss://cdn.proxy.com/pacurl_direct/tls   (传输内容对CDN加密)


需要在命令行运行wssagent软件，示例： ./wssagent-linux  wss://cdn.proxy.com/pacurl_direct/tls  3128

CDN中转翻墙说明详见：https://github.com/httpgate/wssproxy-agent

Firefox设置见上图，选中Manual proxy configuration


## 建立镜像服务器

如果pacurl被封锁，而wssurl可连通，可以用wssurl + /pac, 运行wssagent软件在国内建立镜像服务

用直连wssurl: wss://your.proxy.com/pacurl_direct/pac

用CDN中转wssurl: wss://cdn.proxy.com/pacurl_direct/pac


需要在命令行运行wssagent软件，示例： ./wssagent-linux  wss://cdn.proxy.com/pacurl_direct/pac  443  -s

wssurl + /pac翻墙说明详见：https://github.com/httpgate/wssproxy-agent

Firefox设置同2 用pacurl翻墙，但只能用带用户名密码的pacurl


## 测试

简单验证：https://whatismyipaddress.com/   检查是否是自己的公网IP

性能测试：干净世界 https://www.ganjing.com/ 等视频网站

注意：刚访问一个新网站时会慢一会，打开后就就很快了，https握手时慢