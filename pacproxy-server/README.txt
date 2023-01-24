pacproxy服务器使用

1. 用文本编辑器编辑current.site.cfg, 修改服务器设置, 必须输入域名和管理email
2. 设置路由器端口映射，80端口映射到httpport, 443映射到port
3. 运行对应操作系统的可执行文件， 必要时打开防火墙
4. 查看屏幕输出, 检查各项设置是否正确
5. 从公网访问网站测试没有问题则关掉重新运行一次

如何测试请访问
https://github.com/httpgate/pacproxy.js/blob/main/documents/DeviceSetting_ZH.md

如有疑问请访问
https://github.com/httpgate/pacproxy-server