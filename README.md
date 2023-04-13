# Ubuntu Clash For Windows

#### 1.搜索 `clash for Windows`

#### 2.下载支持Linux版

#### 3.安装准备

+ 软件下载地址

  [https://github.com/Fndroid/clash_for_windows_pkg/releases/download/0.19.20/Clash.for.Windows-0.19.20-x64-linux.tar.gz]()

+ 图片下载地址

  [https://cdn.jsdelivr.net/gh/Dreamacro/clash@master/docs/logo.png]()

#### 4.创建桌面图标

```
# 解压文件
tar -xf Clash.for.Windows-0.19.20-x64-linux.tar.gz
mv 'Clash for Windows-0.19.20-x64-linux' clash
# 桌面配置文件
vim /usr/share/applications/clash.desktop
# 贴入下面内容
[Desktop Entry]
 Name=clash
 Comment=Clash
 Exec=clash所在目录/cfw
 Icon=clash所在目录/clash/logo.png
 Type=Application
 Categories=Development;
 StartupNotify=true
 NoDisplay=false
```



#### 5.选择更多应用

#### 6.点击 profiles 导入节点

#### 7.复制订阅地址,点击 Download 

#### 8.点击 General，打开 Mixin

#### 9.设置代理

#### 10.浏览器上网也需设置代理

#### 11.应用设置代理

##### 1.docker

```shell
mkdir -p /etc/systemd/system/docker.service.d
vim /etc/systemd/system/docker.service.d/http-proxy.conf
# 贴入以下内容
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:7890"
Environment="HTTPS_PROXY=http://127.0.0.1:7890"
# 重启docker
systemctl daemon-reload
systemctl restart docker
```

##### 2.git

```
//设置全局代理
//http
git config --global https.proxy http://127.0.0.1:7890
//https
git config --global https.proxy https://127.0.0.1:7890
//使用socks5代理的 例如ss，ssr 7890是windows下ss的默认代理端口,mac下不同，或者有自定义的，根据自己的改
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890

//只对github.com使用代理，其他仓库不走代理
git config --global http.https://github.com.proxy http://127.0.0.1:7890
git config --global https.https://github.com.proxy http://127.0.0.1:7890
//取消github代理
git config --global --unset http.https://github.com.proxy
git config --global --unset https.https://github.com.proxy

//取消全局代理
git config --global --unset http.proxy
git config --global --unset https.proxy

//解决文件超过大小限制(50M)不能推送到远程仓库
git config --global http.postBuffer 524288000
```

