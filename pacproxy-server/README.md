# pacproxy-server

pacproxy runs in a web server 在vps服务器上运行的pacproxy

自动获取SSL数字证书, 自动加载SSL数字证书

支持多域名，能同时保存和获取多个域名数字证书，但只能启用其中一个域名的https加密

关于pacproxy参见[pacproxy.js](https://github.com/httpgate/pacproxy.js)


## 准备

需要能运行nodejs的服务器, 新手请选用Ubuntu服务器

需要[申请一个域名](https://github.com/httpgate/pacproxy.js/blob/main/documents/About_Domain_ZH.md)，并将域名指向服务器IP

需要ssh到服务器的命令行，新手推荐用Bitvise SSH Client


## 运行(以linux为例)

### 修改网站参数设置current.site.cfg：

```
nano current.site.cfg 
```

### 运行pacproxy服务：

```
./server-linux
```
核对屏幕上显示出的PAC链接，如果不对则需要再修改current.site.cfg

从浏览器访问网站，确认运行正常后 Ctrl + C 退出


### 后台运行pacproxy服务：

```
nohup ./server-linux &
```
防止关闭ssh连接后服务中止, 查看日志：

```
tail -f nohup.out
```

### 停止pacproxy服务

```
ps -ef | grep node
kill -9 找到的pid
```

## 运行(以Windows为例)

用文本编辑器修改 current.site.cfg 后， 双击server-win.exe运行

核对参数正确后，在浏览器访问申请的域名，第一次访问会自动获取数字证书

关闭软件再重新运行，如果运行正常会显示 pacurl, 在浏览器访问 pacurl ， 如正常访问则可以使用