### 获取脚本

```bash
mkdir -p /root/ddns && wget https://raw.githubusercontent.com/zuig/cf-ddns/master/cf-ddns.sh -O /root/ddns/cf-ddns.sh && chmod +x /root/ddns/cf-ddns.sh
```

### 修改配置

```bash
# cloudflare登录邮箱
auth_email="user@example.com"
# Global API Key
auth_key="c2547eb745079dac9320b638f5e225cf483cc5cfdda41" # https://dash.cloudflare.com/profile/api-tokens -> Global API Key
# 主域名
zone_name="example.com"
# 需要DDNS解析域名
record_name="www.example.com"
```

### crontab定时运行

输入crontab -e，然后会弹出vi编辑界面，在里面添加一行：

```bash
*/10 * * * * /root/ddns/cf-ddns.sh >/dev/null 2>&1
```

保存并退出。这里设置每10分钟运行一次cf-ddns.sh脚本，输入service crond status，可以看到contab的运行状态。