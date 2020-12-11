提醒： 免费空间请不要滥用！！！

本项目支持部署kintohub
利用kintohub免费空间部署v2ray和tor，部署成功后，可用v2ray客户端直接访问tor网络，比如暗网.onion，v2ray.json文件中设置了路由分流了tor网络，非tor流量不受影响。

部署服务端
点开 https://app.kintohub.com/ 新建一个APP，点击 Create Service ,然后创建 Web App 如图：
创建 web app

Repository 填上git链接和默认分支master
repository

Build Settings 文件名填写Dockerfile，端口填上8888，填写如下：
build

最后点击右上角 Deploy，部署完成，会生成一个链接，点击链接，如果显示Bad Request，即为成功。

客户端配置
客户端配置看图吧，不多讲：

v2ray

默认UUID：c95ef1d4-f3ac-4586-96e9-234a37dda068

修改UUID
方法一：

v2ray的配置文件config.json，可以改为自己的私密链接，比如 https://gist.github.com/ 里自定义v2ray配置，当然你也可参考本项目的config.json配置，然后生成链接。最后部署的时候写入到Environment variables里，如图：

gist

方法二：

Fork本项目，到config.json里面修改uuid或其它，然后到Dockerfile里面修改ENV CONFIG= 指向链接，例如：ENV CONFIG=https://raw.githubusercontent.com/xuhao4824/kinto/master/config.json指向你自己项目的config.json文件。
