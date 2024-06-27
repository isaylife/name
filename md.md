# 1、安装X-UI面板
```bash
bash <(curl -Ls https://raw.githubusercontent.com/slobys/x-ui/main/install.sh)
```
# 2、输入x-ui自动申请证书
如自动失败可以使用手动
申请成功就安装证书
```
~/.acme.sh/acme.sh --installcert -d 你的域名 --key-file /root/private.key --fullchain-file /root/cert.crt
```
如失败：
3.1安装申请工具
```
curl https://get.acme.sh | sh; apt install socat -y || yum install socat -y; ~/.acme.sh/acme.sh --set-default-ca --server letsencrypt
```
3.2申请证书
```
~/.acme.sh/acme.sh  --issue -d 你的域名 --standalone -k ec-256 --force --insecure
```
3.3安装证书
```
~/.acme.sh/acme.sh --installcert -d 你的域名 --key-file /root/private.key --fullchain-file /root/cert.crt
```
安装完毕记得保存证书路径

# 3、登录xui面板
使用ip+端口登录

# 5、进入面板设置
他会自动保存一下，等待即可。
完毕之后，输入刚刚的密钥和证书文件。保存-重启
然后就能使用域名访问了

# 6、然后搭建vless+reality协议
打开realti就行

指令：
端口放行指令
```
iptables -I INPUT -p tcp --dport 443 -j ACCEPT
```
修改443为自己的端口就行
