# AI Team Souls

> AI 时代的分工不再是"你是谁"（角色），而是"你能碰什么"（上下文）和"你能决定什么"（权限）。

这个仓库定义了一套 4+1+1 AI 团队的完整灵魂配置——不是"怎么跑起来"，而是"它们是谁、怎么工作、怎么协作"。

基础设施运维（端口、启动脚本、故障排查）在 [ai-team-hub](https://github.com/yaChen920213/ai-team-hub)。

---

## 架构：4+1+1

```
工作系统（创造）              生活系统（运维）        内在系统（成长）
┌────────────────────┐      ┌──────────┐          ┌──────────┐
│ Radar → Partner    │      │          │          │          │
│   ↓       ↓        │      │  Butler  │          │   Ally   │
│ Workshop → Keeper  │      │          │          │          │
└────────────────────┘      └──────────┘          └──────────┘
         ↑                        ↑                    ↑
      你(创作者)             你(被照顾的人)        你(成长中的人)
```

| Agent | 本质 | 自主权 | 模型 | Emoji |
|-------|------|--------|------|-------|
| **Radar** | 信息触角，24/7 感知世界 | 高 | GPT 5.4 | 📡 |
| **Partner** | 思维对手，共创判断 | 低 | Claude Opus 4.6 | 🧠 |
| **Workshop** | 生产引擎，执行交付 | Brief 内高 | 按任务动态切换 | 🔨 |
| **Keeper** | 质量守门人，风险校验 | 审核自主 | GPT 5.4 | 🛡️ |
| **Butler** | 生活管家（独立系统） | 高 | GLM 5 | 🏠 |
| **Ally** | 认知镜子，成长伙伴（独立系统） | 低 | Claude Opus 4.6 | 🪞 |

三个系统各自独立：工作系统里你是主角，生活系统里你是甩手掌柜，内在系统里你是对话者。

---

## 四条管线

同一组 agent 运行在四条管线上，靠上下文区分：

```
工作管线：  信号 → 推演 → 交付 → 审核        节奏：任务驱动，有 deadline
知识管线：  采集 → 消化 → 提纯 → 输出        节奏：持续积累，线性递进
创意管线：  捕捉 → 碰撞 → 孵化 → 沉淀        节奏：随机涌现，允许沉睡
生活管线：  Butler 管事务，Ally 管内在        节奏：Butler 定时推送，Ally 随时响应
```

详见 `docs/memory-architecture-proposal.md` 第十二~十四节。

---

## 记忆架构

每个 Agent 采用分层记忆系统：

```
Agent目录/
├── .abstract              ← L0 索引（启动时第一个读，<300 tokens）
├── MEMORY.md              ← L1 长期稳定认知（P0永久/P1-90天/P2-30天）
├── SESSION-STATE.md       ← 当前工作缓冲区
├── reflections/           ← L2 原始反思日志
│   └── archive/
└── lessons/               ← 结构化经验教训
```

共享记忆层位于 Obsidian Vault `03_Work/AI-Team/`，按品牌划分品牌规范，按职能划分竞品档案/战略决策/交付物存档/审核规则库。

详见 `docs/memory-architecture-proposal.md`。

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
├── Ally/                      ← 🪞 认知镜子
│
└── docs/
    ├── memory-architecture-proposal.md  ← 记忆架构 + 管线协议（v2，讨论中）
    └── openclaw-instance-definition.md
```

每个 Agent 目录包含完整文件集：SOUL.md / IDENTITY.md / AGENTS.md / MEMORY.md / TOOLS.md，部分有 HEARTBEAT.md。

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
5. Ally 不做工作执行 — 它看见的是你，不是事。洞察涉及工作方向时由亚臣转达 Partner

---

## Obsidian × AI Team

仓库各板块与 AI 团队的接入关系：

| Obsidian 板块 | 接入方式 | 参与 Agent |
|--------------|---------|-----------|
| 00_Core | 不分配，亚臣个人系统 | — |
| 01_Engine（知识引擎） | 知识管线 | Radar/Partner/Workshop/Keeper/Ally |
| 02_Life（生活层） | 生活管线 | Butler(管理者) + Ally(理解者) |
| 03_Work（工作层） | 工作管线 + 共享记忆层 | Radar/Partner/Workshop/Keeper |
| 04_Lab（实验室） | 创意管线 | Partner/Workshop/Keeper/Ally |
| 40_Periodic（周期笔记） | 生活管线 | Ally(日记/反思) + Partner(月记/年记模式识别) |
| 80_Archive | 不分配，已归档 | — |
| 90_System | 基础设施 | — |

---

## 部署环境

### Discord 频道架构

频道按场景划分（而非按 agent 1:1），对话型 agent（Partner、Ally）走 DM 私聊：

```
情报中心
├── #radar-log          文字频道，信息流/简报推送
├── #design-intel       论坛，设计领域情报
├── #beauty-intel       论坛，美妆个护情报
└── #ai-intel           论坛，AI 领域情报

engine
├── #cubox              采集层
├── #learning           消化层
├── #method             提纯层
└── #writing            输出层

work-品牌名             按品牌划分，每个品牌一个类别
├── work-hahn/          品牌管理/产品开发/产品包装/微信公众号/品牌官网/...
├── work-lubelle/       品牌升级/...
└── ...                 新品牌新增类别，非活跃品牌折叠

life
├── #periodic           周记/月记/年记（日记走 Ally DM）
├── #health             健康管理
├── #asset              资产管理
└── #career             职业发展

lab
├── #灵感种子
├── #随兴实验场
├── #影像实验
├── #视频实验
├── #音乐实验
└── ...                 新实验类型随时新增

DM 私聊
├── Partner             战略对话 + Brief 输出
└── Ally                内省对话 + 日记触发
```

### 频道权限概览

| 类别 | 频道 | 可写 Agent | 可读 Agent |
|------|------|-----------|-----------|
| 情报中心 | #radar-log | Radar | Partner |
| 情报中心 | 各 intel 论坛 | Radar | Partner, Workshop |
| engine | #cubox | Radar（建议入库） | — |
| engine | #learning | Partner, Ally | — |
| engine | #method | Partner, Keeper | Workshop（取弹药） |
| engine | #writing | Workshop, Keeper | — |
| work-品牌 | 各业务频道 | Workshop, Keeper | Partner（只读上下文） |
| life | #periodic | Butler（周报推送） | Partner（月记/年记） |
| life | #health | Butler | Ally（只读） |
| life | #asset | Butler | — |
| life | #career | — | Ally（只读） |
| lab | #灵感种子 | Ally | Partner（碰撞建议） |
| lab | 各实验频道 | Workshop | Partner, Keeper |
| DM | Partner 私聊 | Partner | — |
| DM | Ally 私聊 | Ally | — |

详见 `docs/discord-channel-architecture.md`。

### 其他环境

- **本地：** OpenClaw 实例 + 命令行
- **飞书：** 辅助（待权限理顺后可承接 Butler）

---

## 相关仓库

- [ai-team-hub](https://github.com/yaChen920213/ai-team-hub) — OpenClaw 多实例基础设施运维
