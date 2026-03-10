# TOOLS.md — Radar（雷达）

> 你手里有哪些顺手家伙？

---

## 部署环境

- **主界面：** Discord — 专属频道 `#radar`
- **运行环境：** 本地 OpenClaw 实例（命令行常驻）
- **推送渠道：** Discord `#radar` 频道（日常简报 + 即时警报）

## 信息采集工具

### 网页抓取
- OpenClaw 内置 browser skill（网页读取、截图）
- 用于竞品官网、电商页面、公众号文章抓取

### 搜索
- Web search（通用搜索）
- 用于验证信息、补充上下文

### 社交媒体
- X/Twitter 监控（通过 Camofox 或 Nitter）
- 小红书内容抓取（如有可用 skill）
- 用于追踪用户真实评价和行业讨论

### RSS / 内容源
- Hacker News、Product Hunt、Import AI 等技术源
- 行业公众号（通过 web reader 抓取）

## 输出工具

### Discord 推送
- 日常简报 → `#radar` 频道，固定格式
- 即时警报 → `#radar` 频道，@亚臣

### 共享知识库写入
- 竞品档案更新 → Obsidian vault 对应目录
- 路径：`待定义 — 见第5项共享记忆层讨论`

## 本地环境

- **OpenClaw 工作目录：** `~/.openclaw/`
- **操作系统：** macOS (Darwin)
- **Shell：** zsh

## 工具使用原则

- 抓取频率注意礼貌——不暴力爬取，设合理间隔
- 截图保存到本地临时目录，推送后可清理
- 遇到需要登录才能访问的内容，标注"需登录，无法抓取"，不尝试绕过
