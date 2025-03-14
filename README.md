# serverless-qrcode-hub

苦于微信群聊二维码频繁变动，开发这个能生成永久二维码的工具，不需要服务器。基于 Cloudflare Workers 和 KV 存储实现。

## 功能特性

- 🔗 生成永久短链接，指向微信群二维码
- 🎨 自定义二维码样式和 Logo
- 💻 管理后台可随时更新
- 🔐 密码保护
- 😋 可当短链接生成器
- ☁️ 无需服务器

## TODO

- [ ] 实现定时检查过期短链功能
  - [x] 自动检查过期的短链接
  - [ ] 发送邮件通知管理员
  - [x] 自动清理过期数据
- [ ] 添加访问统计功能
- [ ] 支持批量导入导出
- [ ] 支持多租户
- [ ] 支持多语言
- [ ] 支持多 Serverless 平台

## 使用步骤

1. Fork 本项目
   ![fork](./images/fork.png)
2. 创建 KV 命名空间
   ![create kv](./images/create-kv-space.png)
3. 安装 [Node.js](https://nodejs.org/) (建议 v16 或更高版本)
4. 安装 [pnpm](https://pnpm.io/) 包管理器

## 部署步骤

1. 克隆项目并安装依赖：

   ```bash
   git clone https://github.com/yourusername/serverless-qrcode-hub.git
   cd serverless-qrcode-hub
   pnpm install
   ```

2. 配置 wrangler.toml：

   - 替换 `account_id` 为你的 Cloudflare 账号 ID
   - 替换 `kv_namespaces` 中的 id 为你创建的 KV 空间 ID

3. 设置环境变量：

   ```bash
   # 设置管理后台密码
   wrangler secret put PASSWORD
   # 设置管理员邮箱（用于接收过期通知）
   wrangler secret put ADMIN_EMAIL
   # 设置域名
   wrangler secret put DOMAIN
   ```

4. 部署到 Cloudflare Workers：
   ```bash
   pnpm run deploy
   ```

## 使用说明

1. 访问 `https://your-worker-domain/admin` 进入管理后台
2. 使用设置的密码登录
3. 创建新的短链接，上传群二维码
4. 可选择设置过期时间和自定义二维码样式

## 贡献指南

欢迎提交 Issue 和 Pull Request！
