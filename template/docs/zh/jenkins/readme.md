---
sidebar_position: 1
slug: /jenkins
tags:
  - Jenkins
  - DevOps
---

# 快速入门

[Jenkins](https://www.jenkins.io/zh) 是热门的开源持续集成（CI&CD）软件，提供超过1000个插件来支持构建、部署、自动化，满足各种项目的 DevOps 需要。

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins_is_the_hub_CD_Devops.png)  


## 准备

部署 Websoft9 提供的 Jenkins 之后，需完成如下的准备工作：

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，确保 **Inbound（入）规则** 下的 **TCP:80** 端口已经开启
3. 在服务器中查看 Jenkins 的 **[默认账号和密码](./setup/credentials#getpw)**  
4. 若想用域名访问  Jenkins，务必先完成 **[域名五步设置](./dns#domain)** 过程


## Jenkins 初始化向导

### 详细步骤

1. 使用本地电脑浏览器访问网址：*http://域名* 或 *http://服务器公网IP*, 进入初始化页面
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-installstart-websoft9.png)

2. 运行命令`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`，[获取解锁密码](./setup/credentials#getpw)

3. 成功登录到 Jenkins 后台  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-installcustomer-websoft9.png)

4. 通过 Jenkins 后台，安装所需的插件  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-installing-websoft9.png)

5. 插件安装完成后，创建更多管理员用户  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-installusers-websoft9.png)

> 需要了解更多 Jenkins 的使用，请参考官方文档：[Jenkins 用户文档中心](https://www.jenkins.io/zh/doc/)

### 出现问题？

若碰到问题，请第一时刻联系 **[技术支持](./helpdesk)**。也可以先参考下面列出的问题定位或  **[FAQ](./faq#setup)** 尝试快速解决问题：

**Jenkins 能打开，但总是出现 502 错误？**  

参阅：[此处](./gitlab/admin#502)

**Jenkins 每次启动需等1分钟才能使用？**  

参阅：[此处](./gitlab/admin#502)


## Jenkins 使用入门

下面以 **Github 上的项目通过 Jenkins 自动构建部署** 作为一个任务，帮助用户快速入门：

1. 在 GitHub设置 Personal access tokens，用于 Jenkins 连接
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard2-websoft9.png)

2. Jenkins全局系统设置中，连接 GitHub
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard3-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard4-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard5-websoft9.png)

3. 创建一个构建任务：输入任务名，按流程分别输入 Github项目 URL，账号密码等信息
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard6-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard7-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard8-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard9-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard10-websoft9.png)
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard11-websoft9.png)

4. 在对应Github 项目修改后，push提交；Jenkins完成自动化构建部署
 ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins-wizard12-websoft9.png)

## Jenkins 常用操作

### 安装插件{#installplugin}

登录Jenkins，依次打开：【【Manage Jenkins】>【Plugins Manager】

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins_installemailplugin-websoft9.png)

### 配置 SMTP{#smtp}

下面以提供设置 Jenkins 发邮件的简要步骤：

1. 安装 Jenkins的邮箱扩展插件 [Email Extension](https://plugins.jenkins.io/email-ext/)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins_installemailplugin-websoft9.png)

2. 在邮箱管理控制台获取 [SMTP](./automation/smtp) 相关参数

3. 登录 Jenkins 控制台，依次打开：【Manage Jenkins】>【Configure System】，填写 SMTP 参数
![Jenkins SMTP](https://libs.websoft9.com/Websoft9/DocsPicture/zh/jenkins/jenkins_configuresmtp-websoft9.png)

4. 测试邮件是否可以发送

### 域名额外配置（修改 URL） {#dns}

**[域名五步设置](./dns#domain)** 完成后，需设置 Jenkins URL:

通过SSH连接云服务器，运行下面的 CLI 命令进行参数配置
   
   ```shell
   cd /data/wwwroot/jenkins
   php bin/jenkins config:set web/unsecure/base_url http://www.mydomain.com/ # 修改成您的实际域名，必须以 / 结束
   php bin/jenkins config:set web/secure/base_url http://www.mydomain.com/ # 修改成您的实际域名，必须以 / 结束
   ```

### HTTPS 额外设置{#https}

**[标准 HTTPS 配置](./dns#https)** 完成后，还需运行下面的 CLI 命令进行配置：

```
cd /data/wwwroot/jenkins
php bin/jenkins setup:store-config:set --use-secure=1 --use-secure-admin=1 --base-url-secure="https://www.yourdomain.com/"
php bin/jenkins cache:flush  #将基础URL更改为https并刷新缓存
```

## Jenkins 参数

Jenkins 应用中包含 Nginx, Docker, MongoDB, adminMongo 等组件，可通过 **[通用参数表](./setup/parameter)** 查看路径、服务、端口等参数。

通过运行 `docker ps`，可以查看到 Jenkins 运行时所有的 Container：

```bash
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                NAMES
```


下面仅列出 Jenkins 本身的参数：

### 路径{#path}

* Jenkins 配置文件： */data/apps/jenkins/config.yml*

### 端口

| 端口号 | 用途                                          | 必要性 |
| ------ | --------------------------------------------- | ------ |
| 8080   | Jenkins 原始端口，已通过 Nginx 转发到 80 端口 | 可选   |


### 网址

* Jenkins 后台地址： *URL:端口/administrator*

### 版本

```shell
jenkins -v
```

### 服务

```shell
sudo systemctl start | stop | restart | status jenkins
```

### 命令行

Jenkins 提供 CLI 客户端和 SSH CLI [两种方式](https://www.jenkins.io/zh/doc/book/managing/cli/)，下面是推荐的 客户端 CLI：

```shell
java -jar jenkins-cli.jar [-s JENKINS_URL] [global options...] command [command options...] [arguments...]
```

### API

Jenkins 提供可供远程访问的 [类似 REST API](https://www.jenkins.io/doc/book/using/remote-access-api/) 以便更好的实现自动化。
```
curl JENKINS_URL/job/JOB_NAME/buildWithParameters \
  --user USER:TOKEN \
  --data id=123 --data verbosity=high
```

同时，也提供了 Java, Python, Ruby 等语言的 API SDK 开发包。 

