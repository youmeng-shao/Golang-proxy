# Golang-proxy
## 内容列表
- [背景](#Background)
- [安装](#Install)
- [使用说明](#Usage)
- [运行](#Run)
- [架构图](#Architecture)

## <span id="Background">背景</span>
前后端分离后，前端开发人员可以指定后端地址；后端开发完成后，想测试，虽然可以使用开发环境的前端，但是没有办法使用自己的后端。也有几种办法可以解决：  
1. 将前端代码拉下来，在本地启动前端，并将后端地址指向本地。（每次都要拉取前端代码，并且启动前端也占本地电脑的cpu和内存）
2. 通过proxy软件拦截请求，将部分请求转发到本地后端。比如Http tookit，Burp等。虽然功能强大，但也复杂，最重要一点收费。
  
结合以上几点，决定用Golang写一个简单的Proxy。
## <span id="Install">安装</span>
这个项目使用Golang语言编写的，请确保有Go语言环境。

## <span id="Usage">使用说明</span>
下载压缩包到电脑，并解压；进入proxy文件加下，可以看到有2个文件  
- proxy.go (源码)
- proxy.conf(配置文件)  
  
主要讲解下配置文件配置项：  
listenPort=9999 (proxy监听的本地端口号，必填项)  
/api=http://127.0.0.1:8090 (url中包含/api的请求会转发到127.0.0.1:8090)  
default=https://mgt.orch-test.appexcloudwan.com (如果没有匹配中的url，会被转发到 mgt.orch-test.appexcloudwan.com ， 必填项)  
你甚至可以将配置项中/api=http://127.0.0.1:8090改成/api/clientaccount=http://127.0.0.1:8090，表示只有url中包含/api/clientaccount才会转发到http://127.0.0.1:8090  
## <span id="Run">运行</span>
命令行进入到proxy文件夹下，输入：go run proxy.go  
浏览器输入：http://127.0.0.1:9999  
在终端窗口可以看到请求被代理到的地址

## <span id="Architecture">架构图</span>



