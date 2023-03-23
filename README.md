# 如何部署一个自己的萌翻

# ！！此教程及仓库仍在制作中，请勿参照搭建！！

## TODO:

- [x] OK 自动创建 RabbitMQ vhost
- [ ] 自部署版本的 PS 脚本的升级方案
  - [x] 制作国内镜像，方便大家下载
  - [ ] 删除自部署版本中导出文件打包脚本流程，更新镜像站下载链接
- [ ] 修复导出 to_labelplus 站点名问题
- [ ] 邮件里 site_name 和 site_url 需要优化
- [ ] 支持在配置里设置默认的 admin
- [ ] 基础的后台管理功能
  - [ ] 可用禁止公共注册功能
  - [ ] 通过链接邀请注册功能
  - [x] 管理员管理功能
- [ ] 将自部署版项目组人数上限默认为 100000
- [ ] 在阿里云真实搭建，测试到底什么配置的服务器合适
- [ ] 撰写部署文章

> 此文章包含返佣链接，感谢您的支持

# 最小成本估算

| 项目                   | 每月费用（≈） | 备注                                                                                     |
| ---------------------- | ------------- | ---------------------------------------------------------------------------------------- |
| .com 域名              | 6             | 其他后缀价格不一                                                                         |
| 阿里云 ECS（服务器）   | 17            | 流量费用另算，0.8/元/G                                                                   |
| 阿里云 OSS（图片储存） | 2.4           | 以储存 20G 图片为例，流量费用另算，0.25-0.5/元/G                                         |
| 阿里云 CDN（访问加速） | -             | 用于加速图片访问且预测每张图片会被访问多次，则可以使用，可使图片流量费用降低到 0.15/元/G |

# STEP 1 前置条件

萌翻依赖于阿里云 OSS 对象储存及 CDN 內容分发网络服务，使用其提供的缩略图及鉴权服务。

1. 首先您需要注册一个 <a href="https://www.aliyun.com/?source=5176.11533457&userCode=6ce80f9c" target="_blank" rel="noopener noreferrer nofollow">阿里云账号</a>
1. 购买您的域名，<a href="https://wanwang.aliyun.com/?source=5176.11533457&userCode=6ce80f9c" target="_blank" rel="noopener noreferrer nofollow">域名注册</a>（如果您准备部署在国内服务器以获得国内稳定快速的访问速度，则后续需要备案，必须在国内服务商注册。）
1. 购买 ESC 服务器 TBD
1. 购买域名证书 TBD
1. 绑定 CDN

# STEP 2 服务器部署

1. 将 SSL 证书放置到 certificates 下，并命名为 `cert.key` 和 `cert.pem`
1. 将 `.env.template` 改名成 `.env`，并修改其中配置
1. 使用 `docker-compose up` 启动服务
