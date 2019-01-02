今天克隆速度极为慢，搜了一下原来不止我一个人慢，下面三种方法提速，我折腾了一下，之前一直 clone 不下来，现在我居然 clone 下来了，蛋蛋好疼。

## 中转克隆

借助[coding.net](https://coding.net)的 git 导入功能，通过 git 服务器 clone 你要下载的项目，再从 coding.net 上面下载下来。这是最方便，速度最快的方法。

## 使用翻墙代理

首先你要有代理工具，前提是已经打开了 SS 代理，获取 socks5 的代理地址，通过 git 的内置工具设置代理地址，`127.0.0.1:9742` 这个是我的工具给我分配的端口号码。

```
git config --global http.proxy socks5://127.0.0.1:9742
git config --global https.proxy socks5://127.0.0.1:9742
```

也可以直接修改配置文件 `sudo vi ~/.gitconfig` ，摁`i`进入编辑模式，在最下面添加一段配置代码，按`Esc`退出编辑模式，输入:wq 保存并退出。

```
[http]
    proxy = socks5://127.0.0.1:9742
[https]
    proxy = socks5://127.0.0.1:9742
```

## 修改 host

其实 git clone 或者 git push 特别慢，并不是因为`http://github.com`的这个域名被限制了。而是"`http://github.global.ssl.fastly.Net`这个域名被限制了。那么首先查到这个域名的 ip。然后再 hosts 文件中进行`ip->域名`映射就可以了。这个办法会让 clone 或者 push 速度飞起。在命令行中输入 `sudo vi /etc/hosts` 编辑 hosts 文件，摁`i`进入编辑模式，将下面代码复制下面，按`Esc`退出编辑模式，输入:wq 保存并退出。

```
151.101.72.249 global-ssl.fastly.Net
192.30.253.112 github.com
```

通过 `dig github.com` 查看 IP 地址

```bash
dig github.com

# 输出下面内容
# -----------------------
# ; <<>> DiG 9.8.3-P1 <<>> github.com
# ;; global options: +cmd
# ;; Got answer:
# ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57278
# ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0
#
# ;; QUESTION SECTION:
# ;github.com.            IN  A
#
# ;; ANSWER SECTION:
# github.com.     60  IN  A   192.30.253.112
# github.com.     60  IN  A   192.30.253.113
#
# ;; Query time: 16 msec
# ;; SERVER: 192.168.188.1#53(192.168.188.1)
# ;; WHEN: Wed Mar 22 21:35:21 2017
# ;; MSG SIZE  rcvd: 60
```
