# ChatGPT Next

微信风格的 ChatGPT，基于 Next.js 构建，私有化部署的最佳选择！

https://chatgpt-next.com

备份网址：

- https://chatgpt-next-xcatliu.vercel.app
- https://chatgpt-next.zeabur.app
- https://chatgpt-next-xcatliu.netlify.app

如果你也部署了一个站点并且愿意公开出来，欢迎 pr！

## 特性

- 微信风格的聊天气泡，支持移动/PC 端，打造最极致的交互体验
- 配置密钥别名，无需暴露 apiKey 就可以分享给朋友
- 支持私有化部署，使用 Vercel/Zeabur/netlify 等一键部署

<img src="./public/screenshot-wechat.png" width="390">

## 快速开始

需要先安装 Node.js 环境，可以在[官网下载安装](https://nodejs.org/en/)。

```bash
# 安装依赖
npm i -g pnpm
pnpm i
# 本地开发
pnpm dev
```

### 重要提醒

**中国地区直接请求 OpenAI 接口可能导致封号，所以 dev 环境下跳过了请求。如需发送请求，请将 [app/api/chat/route.ts](https://github.com/xcatliu/chatgpt-next/blob/main/app/api/chat/route.ts) 文件中的相关代码注释掉。**

## 配置

### 配置 apiKey 別名

配置环境变量 `OPENAI_API_KEY_ALIAS` 即可支持 apiKey 别名。

使用 `|` 分隔多项别名配置，每个别名配置使用 `:` 分隔别名和真实 apiKey，举例如下：

```
OPENAI_API_KEY_ALIAS="firstkey:sk-********FUt3|secondkey:sk-********f1J3"
```

按照上面的配置，用户在打开页面的弹窗中输入 `firstkey` 就会以第一个 apiKey 发送请求，输入 `secondkey` 就会以第二个 apiKey 发送请求。

## 交流群

<img src="./public/wechat-group.jpg" width="155">

## 部署

### 使用 [Vercel](https://vercel.com/) 一键部署

1. Fork 本仓库
2. 在 [Vercel](https://vercel.com/dashboard) 中 Add New Project
3. 选择 chatgpt-next 点击 Import 进行导入

### 使用 [Zeabur](https://github.com/zeabur) 一键部署

1. Fork 本仓库
2. 在 [Zeabur](https://dash.zeabur.com) 中创建新服务
3. 选择 chatgpt-next 导入部署

### 使用 [netlify](https://www.netlify.com/) 一键部署

1. Fork 本仓库
2. 在 [netlify](https://www.netlify.com/) 中 Add new site => Import an existing project
3. 选择 chatgpt-next 点击 Deploy site 开始部署

### 运行 docker 镜像

```bash
docker run --name chatgpt-next -d -p 3000:3000 -e OPENAI_API_KEY_ALIAS xcatliu/chatgpt-next:latest
# --name 容器名称，-d 后台运行，-p 端口映射，-e 透传环境变量
```

### 使用 npm script 手动运行

```bash
# 构建
pnpm build
# 启动
pnpm start
```

#### 使用 pm2 后台运行

```bash
# 使用 pm2 后台运行
npm i -g pm2
pm2 start npm --name chatgpt-next -- start
# 一行命令更新应用
git pull && pnpm i && pnpm build && pm2 restart chatgpt-next
```

## 开源协议

MIT，随便拿去用，记得帮我多宣传宣传。

如果觉得帮助到你了，欢迎[请我喝一杯咖啡 ☕️](https://github.com/xcatliu/buy-me-a-coffee)。

---

MIT License

Copyright (c) 2023 xcatliu

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
