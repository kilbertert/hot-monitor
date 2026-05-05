# AI 热点监控工具

输入关键词后，系统会从 Twitter、Bing、HackerNews、搜狗、B 站等 **8+** 数据源聚合抓取热点内容，使用 AI 进行查询扩展、真假识别、相关性分析和摘要生成，并通过 WebSocket 与邮件进行实时通知。同时，项目将热点监控能力封装为 **Agent Skills 技能包**，可直接接入 Cursor、VSCode Copilot、Claude Code 等 AI 编程工具。

## 核心能力

1. **关键词监控管理**：支持创建、激活、暂停监控任务。
2. **AI 热点分析**：自动抓取并分析 8+ 数据源内容，支持扩展查询、真假识别、相关性分析和智能摘要。
3. **多维筛选排序**：支持按来源、重要性、时间范围筛选；按热度、相关性、时间排序。
4. **全网聚合搜索**：输入关键词，一次检索多个信息源。
5. **实时通知机制**：支持 WebSocket 实时推送和邮件通知。
6. **Agent Skills 集成**：可在 Cursor、VSCode Copilot、Claude Code 中直接调用。

## 功能与架构

### 功能模块

![](https://pic.yupi.icu/1/image-20260304101313199.png)

### 架构设计

![](https://pic.yupi.icu/1/image-20260304101440202.png)

## 快速开始

> 详细教程请参考：[本地运行指南](docs/LOCAL_SETUP.md)

### 前置条件

- Node.js >= 18（推荐 20 LTS）
- [OpenRouter API Key](https://openrouter.ai/settings/keys)（必需，用于 AI 分析）

### 1. 配置环境变量

```bash
cp server/.env.example server/.env
```

编辑 `server/.env`，至少填入：

```bash
OPENROUTER_API_KEY=sk-or-v1-你的key
# Twitter API Key（可选）
TWITTER_API_KEY=你的key
```

### 2. 安装依赖

```bash
git clone https://github.com/liyupi/hot-monitor.git
cd hot-monitor
```

后端依赖与数据库初始化：

```bash
cd server
npm install
npx prisma generate
npx prisma db push
```

前端依赖安装：

```bash
cd ../client
npm install
```

### 3. 启动服务（需两个终端）

终端 1（后端，端口 3001）：

```bash
cd server
npm run dev
```

终端 2（前端，端口 5173）：

```bash
cd client
npm run dev
```

启动后访问 [http://localhost:5173](http://localhost:5173) 即可使用。

## 服务地址

| 服务 | 地址 |
| --- | --- |
| 前端页面 | http://localhost:5173 |
| 后端 API | http://localhost:3001 |
| 数据库管理（可选） | `cd server && npx prisma studio` |

更多细节请查看：[保姆级本地运行指南](docs/LOCAL_SETUP.md)。
