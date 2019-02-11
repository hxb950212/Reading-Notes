注: ShadowsocksX 默认本地端口为 1080， ShadowsocksX-NG 默认本地端口为 1086 。
通过

1 、 `lsof -i :1086`

2 、`curl --socks5 127.0.0.1:1086 ip.gs`

3 、`plutil -p ~/Library/Preferences/com.qiuyuzhou.ShadowsocksX-NG.plist | grep "ServerHost\|Password\|Method\|ServerPort\|ShadowsocksOn\|ShadowsocksRunningMode\|LocalSocks5"`

4 、 `tail -n 20 ~/Library/Logs/ss-local.log`

命令看一下端口状态
