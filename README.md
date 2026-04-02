# AI Key Vault

AI Key 管理平台，Docker 部署版本。

## 快速部署

\`\`\`bash
# 克隆代码
git clone https://github.com/chenzai666/ai-key-manage.git
cd ai-key-manage

# 构建并启动
docker compose up -d --build

# 查看状态
docker compose ps

# 查看日志
docker compose logs -f
\`\`\`

## 更新部署

\`\`\`bash
git pull
docker compose up -d --build
\`\`\`

## 访问地址

- 本地：http://127.0.0.1:3000
- 远程：http://<服务器IP>:3000

## 故障排查

| 问题 | 解决方法 |
|------|---------|
| 页面打不开 | 检查容器状态：`docker compose ps` |
| CSS/JS 404 | 确认端口 3000 开放：`ss -tlnp \| grep 3000` |
| 保存按钮无反应 | 浏览器控制台是否有 `crypto.randomUUID` 报错 |
| 容器启动失败 | 查看日志：`docker compose logs` |
| 构建失败 | 确认 Docker 版本 >= 20 |

常用命令：

\`\`\`bash
# 重启
docker compose restart

# 停止
docker compose down

# 强制重建
docker compose up -d --build --no-cache

# 进入容器
docker compose exec ai-key-manage sh
\`\`\`

## 目录结构

\`\`\`
ai-key-manage/
├── Dockerfile          # Docker 镜像构建配置
├── docker-compose.yml  # 容器编排配置
├── app/                # Next.js 前端代码
│   ├── page.tsx        # 主页面（含 UUID polyfill 修复）
│   ├── layout.tsx      # 页面布局
│   └── globals.css     # 全局样式
├── lib/                # 工具函数库
├── public/             # 静态资源
├── next.config.ts      # Next.js 配置
├── package.json        # 依赖声明
└── README.md           # 本文件
\`\`\`

## 环境要求

- Docker 20+
- 端口 3000 开放
