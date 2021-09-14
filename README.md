
This is a template for a web application that authenticates users with [OAuth2](https://datatracker.ietf.org/doc/html/rfc6749).
It uses the following software.
- [OAuth2 Proxy](https://github.com/oauth2-proxy/oauth2-proxy)
- [Nginx](https://www.nginx.com/)
- [Fast API](https://fastapi.tiangolo.com/)
  
# 手順
- Google Cloud Platformで適当なプロジェクトを作成
- Compute Engineで適当なVMインスタンスを起動(http,httpsは許可する)
- [VPCネットワーク]>[外部IPアドレス]  
static IPを予約して割り当てる

```bash
> wget https://github.com/oauth2-proxy/oauth2-proxy/releases/download/v7.1.3/oauth2-proxy-v7.1.3.linux-amd64.tar.gz
> tar -zxvf oauth2-proxy-v7.1.3.linux-amd64.tar.gz
> sudo mv oauth2-proxy-v7.1.3.linux-amd64/oauth2_proxy /usr/local/bin/
```
```
[Unit]
Description=OAuth2 Proxy
After=network.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/local/bin/oauth2_proxy -cookie-secret=foo -email-domain=* -provider=google -client-id=bar -client-secret=baz

[Install]
WantedBy=multi-user.target
```