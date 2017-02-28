# Https

SSL证书需要向国际公认的证书证书认证机构（简称CA，Certificate Authority）申请。  

## SSL 证书类型
CA机构颁发的证书有3种类型：  
- 域名型SSL证书（DV SSL）：信任等级普通，只需验证网站的真实性便可颁发证书保护网站；  
- 企业型SSL证书（OV SSL）：信任等级强，须要验证企业的身份，审核严格，安全性更高；  
- 增强型SSL证书（EV SSL）：信任等级最高，一般用于银行证券等金融机构，审核严格，安全性最高，同时可以激活绿色网址栏。  
扩展证书 (EV) 是可用的最高等级 SSL 证书。虽然该证书与其他 SSL 使用同样强大的加密技术，但获取这样一个证书需要严格的审查过程。您获得的是一个显眼的绿色地址栏，可使访问者立即产生安全感。如果您接受在线支付，EV 是您的最佳选择。


## SSL 产品

### 多域名 SAN SSL 证书
- 使用更少的成本，保障您的所有网站的安全。
- 主题备用名称 (SAN) SSL 证书和其他 SSL 提供的加密服务相同，但可以保护多个网站。因此，您可以使用一个 SAN 证书保障 LilysBikes.com、LilysBikeShop.com 和 Lilys.bike 的安全。您的客户提交到其中的任意一个网站的信息都将获得安全保护。  
这些类证也称为多域名或统一通信证书 (UCC) SSL。  
- 统一通信证书 (UCC) 是保护一个域名下的多个域名和多个主机名的 SSL 证书。  
UCC SSL 让您能够仅凭一个 SSL 就可保护一个主域名和多达 99 个其他的主题备用名称 (SAN)。
例如，您可以使用 UCC 来保护 www.domains1.com、www.domains2.net 和 www.domains3.org。

### 通配型 SSL 证书
无限个服务器。无限个子域名。绝对节省费用。
通配型 SSL 证书可加密提交至单个网站或其任何相关网页（子域名）的所有信息。您只需支付一个 SSL 证书的费用即可保护 lilysbikes.com（网站）、mobile.lilysbikes.com（子域名）和 shop.lilysbikes.com（子域名）。而且只需安装和管理一个 SSL。

### 如何安装我的 SSL 证书？
- 生成证书签名申请
要安装数字证书，您必须先生成证书签名申请 (CSR) 并将其提交给证书颁发机构 (CA)。CSR 包含您的证书申请信息（包括您的公用密钥）。您应该使用您的 Web 服务器软件生成 CSR，这样还会创建用于加密和解密安全交易的公用/私有密钥对。  
注意：生成您的 CSR 时，请指定大小至少为 2048 的密钥。
- 生成 NGINX CSR（证书签名申请）

### 苹果系统对ssl的支持


#### 阿里云申请免费https
1. 登陆阿里云后台管理控制台
2. 选择产品与服务——安全——证书服务
3. 购买证书——免费型DV SSL(赛门铁克)——购买
4. 我的证书列表——补全信息
5. 输入具体子域名信息 eg. aa.bb.cc.com
6. 填写个人信息, 注： 域名验证类型 选用了默认的 DNS
7. 选择系统生成CSR，点创建，点生成
8. 点击进度，查看需要在DNS服务上配置的信息,新增DNS配置
9. 审核成功后，点击下载相应的证书
10. 服务器配置,参见下

#### Nginx 配置

- Demo 通过nginx设置https请求的version路由
```    
server {
        listen 443;
        #listen [::]:443;

        server_name xxx.xxx.com;

        # access log file
        access_log /dir/to/ssl.log;

        ssl on;
        ssl_certificate /dir/to/cert.pem;
        ssl_certificate_key /dir/to/cert.key;

        set $version_router "http://127.0.0.1:1001";
        # 设置API版本路由, 注意if后面要有空格, =号左右要有空格
        if ($http_private_header = "2.1" && ){
                set $version_router "http://127.0.0.1:1002";
        }

        location / {

                proxy_pass $version_router;

                # Use public headers
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

                # Mark request as https
                proxy_set_header X-Request-Port 443;

                # Use private headers
                proxy_set_header X-Test-1 $http_x_docchat_app_version;
                proxy_set_header X-Test-2 $version_router;
              }

}    

```

- 重启Nginx服务

```
/usr/sbin/nginx -s reload
```

## Refs
- [SSL服务对比](https://www.zhihu.com/question/19578422)
- [SSL证书帮助](https://sg.godaddy.com/zh/help/ssl-1000006)
- [Ali Https ](https://promotion.aliyun.com/ntms/act/globalhttps.html)
- [苹果 ATS](https://help.aliyun.com/knowledge_detail/48151.html)
