---
title: GRPC微服务电商项目 - yg 校园易购
date: 2024-11-12 13:14  
categories:
- Go
- Vue
- Docker
- Linux
- Git
tags:
- Go
- Vue
- Docker
- Linux
- Git
- GRPC
---


## yg 校园易购

适合于学习微服务架构的实战项目，采用微服务架构的方式来写这个系统的相关功能，包括用户服务、商品服务、库存服务等等。

注：详细配置信息，在文章后边nacos配置以及其他配置。

![校园易购logo](/docs/img/page3/projects/nacos/b2.png)

## 一、技术栈简介

采用微服务架构的方式来写这个系统的相关功能，包括用户服务、商品服务、库存服务等等。

- Golang 1.22.3
- Gin
- Mysql 8.0
- Redis
- Nodejs 14.21.3（建议使用 14.21.3 下载，并且使用淘宝镜像）
- Vue
- gRPC
- Consul
- Nacos

点击跳转 Git：[GIthub 地址](https://github.com/xzhHas/yg)

## 二、快速开始

> 安装本系统使用到的插件，这里推荐使用 docker 安装，此操作皆在 ubuntu 系统下操作，如果是其他系统只需要修改一下命令即可。

1、docker 安装 Mysql8.0

2、docker 安装 Redis

3、docker 安装 Nacos

4、docker 安装 Consul

5、docker 安装：Elasticsearch、kibana 及 ik 的安装

**搭建系统详解网址：** [CSDN 网站搭建前的准备教程](https://blog.csdn.net/m0_73337964/article/details/139523540)

### 1、前端的配置

采用 vue 搭建一套后台管理系统和一套电商系统。

1、获取 vue 所需要的依赖：

```
npm insatll
```

2、启动 vue 项目：

```
npm run dev
```

### 2、后端的配置

1、protobuf 的配置

我已经把文件复制到 docs/protobuf 文件下了，把他们直接复制到你的 go 安装目录的 bing 文件夹下即可。

然后在每一个文件目录下的 proto 文件下，在终端输入(生成所需要的 proto 文件)：

```
protoc --go_out=. --go-grpc_out=. *.proto
```

2、修改`config-pro.yaml`文件里面的信息为 nacos 的模式即可。

3、最后，在每一个还有 main.go 的目录下进行终端启动：

```
go mod tidy
go build
./xxx.exe
```

注：这里我是打算写一个脚本一键启动的，但是还没完成，后续会修改的。

### 3、启动

此时，前端和后端都已经启动了，就可以点开浏览器去测试一下了。

http://xxxxxxxx:8089

http://xxxxxx:8090

## 三、数据库设计

![校园易购logo](/docs/img/page3/projects/nacos/b1.png)

## 四、核心系统功能

1 用户功能

2 用户操作功能

3 库存服务

4 商品服务

5 订单服务

## 五、效果演示

[前台商城系统&后端管理系统](https://github.com/xzhHas/yg)

## 六、可能出现的问题

1、在使用 oss 服务的时候可能出现服务未发现的问题，这是因为 oos 的回调服务必须是公网 IP，如果你用的本地计算机，那么就需要内网穿透解决。

2、在使用阿里云支付的回调服务同上，也许哟啊内网穿透。

3、使用 ubuntu 系统，在本地可能无法访问虚拟机的 IP 地址或者连接不上，请修改虚拟机为桥接模式。

4、前端在 npm insatll 的时候报错，请看错误信息，出现错误的极大概率就是本地的微软运行库不全，那你自己在网上找一个修复一下就可了。

## 七、最后

感谢大家观看我的内容。


### 环境搭建教程

CentOS7 参考地址：https://blog.csdn.net/qq23001186/article/details/125693739

putty 参考地址：https://blog.csdn.net/qq23001186/article/details/125696001

git 参考地址：https://blog.csdn.net/qq23001186/article/details/125695151

docker 参考地址：https://blog.csdn.net/qq23001186/article/details/125695822

mysql 参考地址：https://blog.csdn.net/qq23001186/article/details/125696882

Go 参考地址：https://blog.csdn.net/qq23001186/article/details/125697346

Nodejs 参考地址：https://blog.csdn.net/qq23001186/article/details/125698420

grpc 参考地址：https://blog.csdn.net/qq23001186/article/details/125729248

YApi 参考地址：https://blog.csdn.net/qq23001186/article/details/125832921

redis 参考地址：https://blog.csdn.net/qq23001186/article/details/126023939

consul 参考地址：https://blog.csdn.net/qq23001186/article/details/126025565

nacos 参考地址：https://blog.csdn.net/qq23001186/article/details/126084869

ES+kibana+IK 参考地址：https://blog.csdn.net/qq23001186/article/details/126324385

rocketMq 参考地址：https://blog.csdn.net/qq23001186/article/details/126337637

kong 参考地址：https://blog.csdn.net/qq23001186/article/details/126357870

jenkins 参考地址：https://blog.csdn.net/qq23001186/article/details/126372380

原文链接：https://blog.csdn.net/qq23001186/article/details/125699240


### Nacos部署

原创 席万里 席万里要学习 2024 年 06 月 07 日 13:07

主要给大家讲一下怎么将配置文件的信息导入到 nacos 中去。

登录密码和账号都是 nacos，直接登录就可以了。

![alt text](/docs/img/page3/projects/nacos/a1.png)

1、我们登录进去之后可以看到左侧有命名空间的字样，我们就在右上角去创建新的命名空间，如下：

![alt text](/docs/img/page3/projects/nacos/a2.png)

2、然后我们找到上面的配置管理->配置列表，我们可以看到主页面上面已经有了我们的各个命名空间，然后我们点击最右边的+号，添加信息：

![alt text](/docs/img/page3/projects/nacos/a3.png)

3、在后端我们使用了 yaml 文件，在 nacos 配置的时候一些信息要映射正确：

![alt text](/docs/img/page3/projects/nacos/a4.png)

![alt text](/docs/img/page3/projects/nacos/a5.png)

内容就是我们要配置的信息了，所有的配置信息如下（你自己配置就可了，不懂的话私信我）：

注：以下所有的 Group 我都使用 pro 了，如果要使用 dev 的话 自己克隆改一下就可以了。

1、用户服务

user-srv.json

```
{
    "name":"user-srv",
    "mysql":{
        "host":"127.0.0.1", #修改为你的IP地址
        "port":3306,
        "db":"mxshop_user_srv",
        "user":"root",
        "password":"xiwanli"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    }
}
```

user-web.json

```
{
    "name":"user-web",
    "host":"192.168.3.152",
    "port":8024,
    "user_srv":{
        "host":"192.168.3.152",
        "port":50051,
        "name":"user-srv"
    },
    "jwt":{
        "key":"asdfasdfFDSF4r32#04#"
    },
    "sms":{# 短信服务 阿里云的自己操作一下，暂时也可以不用操作（不对程序有大影响）
        "key":"",
        "secrect":""
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "redis":{
        "host":"192.168.3.200",
        "port":6379,
        "expire":300
    }
}
```

2、库存服务

inventory-srv.json

```
{
    "name":"inventory-srv",
    "tags":["inventory-srv","xiwanli"],
    "host":"192.168.3.152",
    "mysql":{
        "host":"127.0.0.1",
        "port":3306,
        "db":"mxshop_inventory_srv",
        "user":"root",
        "password":"xiwanli"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    }
}
```

3、用户操作服务

userop-srv.json

```
{
    "name":"userop-srv",
    "tags":["userop-srv","xiwanli"],
    "host":"192.168.3.152",
    "mysql":{
        "host":"127.0.0.1",
        "port":3306,
        "db":"mxshop_userop_srv",
        "user":"root",
        "password":"xiwanli"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    }
}
```

userop-web.json

```
{
    "name":"userop-web",
    "host":"192.168.3.152",
    "port":8025,
    "tags":["userop-web","xiwanli"],
    "userop_srv":{
        "name":"userop-srv"
    },
    "goods_srv":{
        "name":"goods-srv"
    },
    "jwt":{
        "key":"asdfasdfFDSF4r32#04#"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    }
}
```

4、商品服务

goods-srv.json

```
{
    "name":"goods-srv",
    "tags":["goods-srv","xiwanli"],
    "host":"192.168.3.152",
    "mysql":{
        "host":"127.0.0.1",
        "port":3306,
        "db":"mxshop_goods_srv",
        "user":"root",
        "password":"xiwanli"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "es":{
        "host":"192.168.3.200",
        "port":9200
    }
}
```

goods-web.json

```
{
    "name":"goods-web",
    "host":"192.168.3.152",
    "port":8021,
    "tags":["goods-web","xiwanli"],
    "goods_srv":{
        "name":"goods-srv"
    },
    "inventory_srv":{
        "name":"inventory-srv"
    },
    "jwt":{
        "key":"asdfasdfFDSF4r32#04#"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "jaeger":{
        "host":"192.168.3.200",
        "port":6831,
        "name":"mxshop"
    }
}
```

5、oss 服务

oss-web.json

```
{
    "name":"oss-web",
    "host":"192.168.3.152",
    "port":8023,
    "tags":["oss-web","xiwanli"],
    "jwt":{
        "key":"asdfasdfFDSF4r32#04#"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "oss":{
        "key":"",
        "secrect":"",
        "host":"http://mxx-shop.oss-cn-beijing.aliyuncs.com",
        "callback_url":"http://vuau2r.natappfree.cc/oss/v1/oss/callback",
        "upload_dir":""
    }
}
```

6、库存服务

order-srv.json

```
{
    "name":"order-srv",
    "tags":["order-srv","xiwanli"],
    "host":"192.168.3.152",
    "mysql":{
        "host":"127.0.0.1",
        "port":3306,
        "db":"mxshop_order_srv",
        "user":"root",
        "password":"xiwanli"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "goods_srv":{
        "name":"goods-srv"
    },
    "inventory_srv":{
        "name":"inventory-srv"
    }
}
```

order-web.json

```
{
    "name":"order-web",
    "host":"192.168.3.152",
    "port":8022,
    "tags":["order-web","xiwanli"],
    "order_srv":{
        "name":"order-srv"
    },
    "goods_srv":{
        "name":"goods-srv"
    },
    "inventory_srv":{
        "name":"inventory-srv"
    },
    "jwt":{
        "key":"asdfasdfFDSF4r32#04#"
    },
    "consul":{
        "host":"192.168.3.200",
        "port":8500
    },
    "alipay":{ # 自己修改一下
        "app_id":"90210d01015640880",
        "private_key":"MIIEpQIBAAKCAQEAptrdcXYZq6whaQSwjePqOIsI4kX2WVXr9BYaZw6no1v/6t6J4W1K0+OgqPiyxWPl5kImUu+fukCgd20sI20vgXdi7hDeZMEfe1UMTlHrrLg5i0IXYLCC2IdWScYcM4UdOCtQlvJSEpg/GX1n4dIOZ4RsRCmw62Rsy+B3clh6NbhiLtg+HO8C9qiNukceK9L4Q6JH3c6HiJWnA8dyQ1uHwG9jvZmU+YTbj0FiETPtCDkZYfetjLGpB9vcJgm0aJtPcHdtHoJdwchznGmZ2lrBgHMt6wpr221vHE+tXhoI5hj4NRl+K0vnRl3TUVXxRvM18ULPfUSsstR4QQqpgU+Nw8QIDAQABAoIBAQCcOG36Ys/YHoniWyEbM/vAL3gnQB5xCiW79rogqASIyEJFjKiDWHx4T2a9r7qcQ3e+DBJlnFGQRv8tQqOYLwJy22k18ZhLy/6mTZcXfb6T8IQ0GBy9tCLSqtPh10AH7Gr1WIu8dJF9qWdh/yrQbCa2zFC4IX03qG+gPtU4+IISgQTPwZvjD9qk8ZA5n7d9eUzMYrdztStBz+Mmi/PjFWlilxfggIowU7qUVhXxN1WKWW+nV5sdGWXU16Rl/paGOVjL0sLPlECHrup++2vMdfyyq4a7gG0yl2gIEkWQJapR+6YWXI3Uc1PYlvLfrzD5/PpYOz7bWUBNycdWwUpW/RUBAoGBAN3sGVhrOMp+pnxdLb+oMgZqJR4PrAZ9fPu6pDT3oQD5Nm0ii4OqbfNjYhTZ/7hdsTVjPI83uBDpStXlp9NOr+392gWdkvcbFru+/uuEIWyjcKrDw62tn7aZMZ+7oiUdHn6QfvwG+J+WgVVHkX4cGoUbVxugPj88jpWtHJ+5olAoGBAMB6B+QH9Ezu9VkXw3GYCsNgp7W3neGRYeb3VzjlsKCqnB+jaBH1Ex+nTXBrhHzuzRoFwj41OltQ1lnwVWmJPPeEBTO3fV1A7lRJJ/LofwaHiffRayzt5iQ9mlqHEs4Kht3Fpyg7Zpt6T+sfGqBVKKg2Rzt335aH0+DQKbPz8jPdAoGBANSkAbUjKAt/R28qqUdXlndnBaHESoT9gOCDegv2qqMQKAJyc1P53di0haqNJ+Y0gDQznjdsoEY0A6zonOJwJ0rXTizLS6LSpfnHjOOGe7Bo+u/lHH4yOzLvnwj69O46EcwbdsJQDAfUINKGfaZ6J6sz6Pb+vco0hcchMhCKhTaxAoGATkrVHtplc03YGu9hnrk715FfZrlTzUc3zZ1aq1gy6oe7jdsIIBXSO5PwGgSCFdeFMkqZYniATlipeFgcRht+4yeefhTrN52L1FkVmOcdlGhZpKZYtCPo82DjgmNjMNBzX45gmirfZ+ruyzMRv5okOZgqjXQLTM3fT5kc/YgDQzkCgYEAxcpIpcoa29ga9dJqbw/HToEWwfG2mJGWWhQrB9ySRa0QxgFoOZzDln1KCN/ck/7iEW9f2vEfxjluzbPQmPodsJrEWrs/hP3iQDoZUvWt8RIqcC5h1JxpoA5FOkBUEI/xbAt/ypPmP1gbNl01IUPONYDEYx0UzPqh6j15tEKM02o=",
        "ali_public_key":"MIIBIjANBgkqhkiG9w0BAQEFAAOCAQa8AMIIBCgKCAQEApb5zaEYrOgB9s8gX7yNGbF86nF8BvUjT0f01no0I2HDNvXjuQrYdmiHz8xfxCdysvUeTR4SURru6LYus3e8JB+l2TdmWPzrPjcdefxV5PSpIR6A/6xGkeKOxacKbYSMvt3t98Ge4GAovAatV5hM6t77UhmlC1jWmwCkEeD2t21kLbxl70v2I8ztsqlbH1jzEPeyHF02p11kYPjJ+Vte4M+vMbX4fDxBjABUBCVMRURRDXCcbD+lzRMTyoGiDxdU4MXJGYS/HBaQgrEsK1GoTkuv/2XB0jfdHmIa89cJvMvGle5WNlTfn4T6+2PbsrvS0XJYhcTIY0pv8wwkf6hCMHwIDAQAB",
        "notify_url":"http://echmjv.naappfree.cc/o/v1/pay/alipay/notify",
        "return_url":"http://192.18.3.152:8022/"
    },
    "jaeger":{
        "host":"192.68.3.200",
        "port":6831,
        "name":"mxshop"
    }
}
```

到这里就结束了，感谢大家的观看。
