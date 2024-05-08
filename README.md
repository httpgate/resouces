# resouces

pacproxy compiled executable programes and manuals

pac加密代理服务器，编译好的绿色可执行程序和说明文档

服务器软件在[pacproxy-server文件夹](pacproxy-server)

客户端软件wssagent在[wssproxy-agent文件夹](wssproxy-agent)


## 推荐

推荐用prcproxy安全的访问以下网站：
* 明慧网：https://www.minghui.org
* 干净世界：https://www.ganjing.com
* 神韵作品: https://shenyunzuopin.com
* 大法经书: https://www.falundafa.org


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

pacurl1 :  https://your.proxy.com/pacurl_direct         (超过两个小时不上网需要关闭和重新打开浏览器)

pacurl2 :  https://your.proxy.com/pacurl_need_password  (浏览器会提示输入用户密码）

   用户/密码：proxy_user / proxy_pass  （需要在2分钟内输入正确用户密码，否则需要关闭重新打开浏览器）

可以直接将pacurl设置在Firefox浏览器内，或wifi网络设置上，无需安装翻墙软件即可翻墙

pacurl翻墙说明详见： https://github.com/httpgate/pacproxy.js/blob/main/documents/DeviceSetting_ZH.md

Firefox设置：

![Firefox设置图](Firefox.JPG)

主流浏览器都支持pacproxy, 其他软件很多只支持普通proxy, 可以用[Stunnel](https://www.stunnel.org/)或类似软件将pacproxy转为普通的内网proxy。

Stunnel的参考设置为：

```
foreground = yes

[example-proxy]
client = yes
accept = 127.0.0.1:8080
connect = your.proxy.com:443
# Android暂不支持数字证书验证
# veryfychain = yes
```
pacurl1 需要改为：http://127.0.0.1:8080/pacurl_direct

pacurl2 需要改为：http://127.0.0.1:8080/pacurl_need_password

建议使用[wssagent客户端软件](https://github.com/httpgate/wssproxy-agent)，比stunnel更安全方便，如下所示：

## 用websocket url (简称wssurl)翻墙：

运行服务器后，服务器还会显示以下wssurl:

直连wssurl1:  wss://your.proxy.com/pacurl_direct   （用于全局代理，可让聊天软件等翻墙)

直连wssurl2:  wss://your.proxy.com/pacurl_direct/tls  （用于域名伪装时的tls验证)

在命令行运行wssagent软件，示例： ./wssagent-linux  wss://your.proxy.com/pacurl_direct  3128

Firefox设置见上图，选中Manual proxy configuration


## 用支持websocket的CDN中转翻墙

可以在类似cloudflare的支持websocket的CDN创建一个域名，如cdn.proxy.com，并将域名指向代理服务器的IP地址

CDN中转 wssurl1:   wss://cdn.proxy.com/pacurl_direct   （CDN能知道访问的网址和http传输内容）

CDN中转 wssurl2:   wss://cdn.proxy.com/pacurl_direct/tls   (传输内容对CDN保密)

在命令行运行wssagent软件，示例： ./wssagent-linux  wss://cdn.proxy.com/pacurl_direct/tls  3128

Firefox设置见上图，选中Manual proxy configuration


## CDN中转加密pacprxy代理

一般情况下利用wssagent和CDN中转的wssurl会将加密代理转换成本地非加密代理，在某些不安全的设备和网络上，可能希望在Firefox上设置加密pacurl实现端到端加密，则可在 wssurl后加 /pac

用CDN中转wssurl: wss://cdn.proxy.com/pacurl_direct/pac   (传输内容对CDN，本地网络，本设备保密，仅Firefox解密)

在命令行运行wssagent软件，示例： ./wssagent-linux  wss://cdn.proxy.com/pacurl_direct/pac  443  -s

Firefox设置同2 用pacurl翻墙，但只能用需要输入户名密码的pacurl_need_password

需要本机hosts文件加一条记录： 127.0.0.1  your.proxy.com

也可以使用类似nextdns这样的Private DNS加密DNS服务，如果nextdns被封锁，可参考[CDN中转DOH服务](https://github.com/httpgate/wssproxy-agent/blob/main/CDN_PROXY_DOH.md)

## 测试

简单验证：https://whatismyipaddress.com/   检查是否是自己的公网IP

性能测试：干净世界 https://www.ganjing.com/ 等视频网站

注意：刚访问一个新网站时会慢一会，打开后就就很快了，https握手时慢

以上这些繁复的功能只是为了应对一些极端的封锁情况，使用任何一种方法可以安全上网以后就不需要花时间研究其他的方法。
