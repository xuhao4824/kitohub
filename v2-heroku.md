Deploy
提醒： 滥用可能导致账户被BAN！！！

Heroku上部署v2ray和tor，部署成功后，可用v2ray客户端直接访问tor网络，比如暗网.onion，v2ray.json文件中设置了路由分流了tor网络，非tor流量不受影响。

部署服务端
点击上面紫色Deploy to Heroku，会跳转到heroku app创建页面，填上app的名字，然后换上从 https://www.uuidgenerator.net/ 拷贝过来的UUID，点击下面deploy创建APP，完成后会生成一个链接，点击链接显示“Bad Request”就说明部署成功了！

需要记下的是appname,和你填入的UUID，下面就可以设置客户端翻墙了。

客户端设置
443port

上图是443端口设置方法，当然你也可以设置80端口，不要打开tls就可以了，如下：

地址(address) : appname.herokuapp.com	//appname替换成你的app名字

端口(port) : 80

用户ID(uuid) : 这里填写刚申请的UUID

加密方式(security) : aes-128-gcm

传输协议(network) : ws
本地客户端config.json文件配置：

{
  "inbounds": [
    {
      "port": 1080,
      "listen": "127.0.0.1",
      "protocol": "socks",
      "sniffing": {
        "enabled": true,
        "destOverride": ["http", "tls"]
      },
      "settings": {
        "auth": "noauth",
        "udp": false
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "appname.herokuapp.com",  //域名
            "port": 443,
            "users": [
              {
                "id": "3bbb0791-59d0-4256-b21c-c33d3c1737a3"
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "wsSettings": {}
      }
    }
  ]
}
