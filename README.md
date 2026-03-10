# AI Team Souls

> AI 时代的分工不再是"你是谁"（角色），而是"你能碰什么"（上下文）和"你能决定什么"（权限）。

这个仓库定义了一套 4+1 AI 团队的完整灵魂配置——不是"怎么跑起来"，而是"它们是谁、怎么工作、怎么协作"。

基础设施运维（端口、启动脚本、故障排查）在 [ai-team-hub](https://github.com/yaChen920213/ai-team-hub)。

---

## 架构

```
Radar → Partner → Workshop → Keeper
  │        │         │          │
感知信号  共创判断   生产交付   风险校验
  │        │         │          │
  └──→ 你 ────→ 你可中途介入 ──→ 你最终拍板
```

| Agent | 本质 | 自主权 | Emoji |
|-------|------|--------|-------|
| **Radar** | 信息触角，24/7 感知世界 | 高 | 📡 |
| **Partner** | 思维对手，共创判断 | 低 | 🧠 |
| **Workshop** | 生产引擎，执行交付 | Brief 内高 | 🔨 |
| **Keeper** | 质量守门人，风险校验 | 审核自主 | 🛡️ |
| **Butler** | 生活管家（独立系统） | 高 | 🏠 |

---

## 目录结构

```
├── AI-Team-Architecture.md    ← 总纲：原则 / 架构 / 规则 / 演化路径
├── USER.md                    ← 共享用户画像（所有 agent 共用）
├── ROUTING.md                 ← 协作路由规则
│
├── Radar/                     ← 📡 感知信号
│   ├── SOUL.md                    我是谁
│   ├── IDENTITY.md                身份证
│   ├── AGENTS.md                  我怎么工作
│   ├── HEARTBEAT.md               我平时怎么活
│   ├── MEMORY.md                  我记住什么
│   └── TOOLS.md                   我手里有什么
│
├── Partner/                   ← 🧠 共创判断
├── Workshop/                  ← 🔨 生产交付
├── Keeper/                    ← 🛡️ 风险校验
├── Butler/                    ← 🏠 生活管家
│
└── docs/                      ← 参考文档
    └── openclaw-instance-definition.md
```

---

## 核心设计原则

**拆分检验标准** — 只有四个理由值得把一个 agent 拆成两个：

| 维度 | 问题 |
|------|------|
| 上下文冲突 | 两件事需要的背景信息是否互相干扰？ |
| 自主权不同 | 一件事可以放手，另一件不行？ |
| 时间节奏不同 | 一件是 24/7，另一件按需？ |
| 失败代价不同 | 一件做错可重来，另一件不可逆？ |

**系统规则：**

1. Partner 不直接替代 Workshop — 输出物永远是 brief，不是成品
2. Keeper 必须真有否决权 — 否则只是礼仪，不是门卫
3. Workshop 在关键节点强制暂停 — 不是"可以"介入，是"必须"等确认
4. Partner 无自主调度权，但有经亚臣确认后的传话权 — 决策是你做的，它只传递

---

## 部署环境

- **Discord：** 6 个频道（`#radar` `#partner` `#workshop` `#keeper` `#butler` `#general`）
- **本地：** OpenClaw 实例 + 命令行
- **飞书：** 辅助（待权限理顺后可承接 Butler）

---

## 相关仓库

- [ai-team-hub](https://github.com/yaChen920213/ai-team-hub) — OpenClaw 多实例基础设施运维
