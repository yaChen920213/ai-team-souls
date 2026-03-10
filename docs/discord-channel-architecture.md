# Discord 频道架构

> 频道按场景划分，不按 agent 1:1 对应。对话型 agent（Partner、Ally）走 DM 私聊。

---

## 设计原则

1. **场景驱动**：频道代表"在做什么"，不代表"找谁聊"
2. **对话走私聊**：Partner 和 Ally 是深度对话型 agent，DM 比频道更自然、更私密
3. **与 Obsidian 对齐**：频道类别与 Obsidian 仓库板块一一对应
4. **按需增长**：新品牌、新实验类型随时新增频道/类别，非活跃的折叠

---

## 频道结构

### 情报中心（类别）

| 频道 | 类型 | 用途 | 对应 Obsidian |
|------|------|------|-------------|
| `#radar-log` | 文字频道 | Radar 推送日常简报 + 即时警报 | — |
| `#design-intel` | 论坛 | 设计领域情报，每条情报一个帖子 | 01_Engine/10_Cubox |
| `#beauty-intel` | 论坛 | 美妆个护行业情报 | 01_Engine/10_Cubox |
| `#ai-intel` | 论坛 | AI 领域情报 | 01_Engine/10_Cubox |

论坛格式适合情报类内容：每条一个帖子，天然带讨论串，不会淹没在时间线里。

### engine（类别）

| 频道 | 用途 | 对应 Obsidian |
|------|------|-------------|
| `#cubox` | 采集层协作：素材入库讨论 | 01_Engine/10_Cubox |
| `#learning` | 消化层协作：阅读讨论、概念拆解 | 01_Engine/20_Learning |
| `#method` | 提纯层协作：方法论打磨、SOP 审核 | 01_Engine/30_Method |
| `#writing` | 输出层协作：个人内容生产、发布前审核 | 01_Engine/40_Writing |

### work-品牌名（每个品牌一个类别）

按品牌划分类别，每个品牌下按业务场景建频道：

**work-hahn：**
| 频道 | 用途 |
|------|------|
| `#品牌管理` | 品牌规范维护、视觉管理 |
| `#产品开发` | 新品策划、配方讨论 |
| `#产品包装` | 包装设计、文案审核、生产稿 |
| `#微信公众号` | 公众号内容策划与生产 |
| `#品牌官网` | 官网内容与设计 |
| ... | 按需新增 |

**work-lubelle：**
| 频道 | 用途 |
|------|------|
| `#品牌升级` | 品牌升级项目 |
| ... | 按需新增 |

品牌数量增长时，非活跃品牌的类别折叠即可。

### life（类别）

| 频道 | 用途 | 对应 Obsidian |
|------|------|-------------|
| `#periodic` | 周记/月记/年记推送和讨论（日记走 Ally DM） | 40_Periodic |
| `#health` | 健康管理：追踪、提醒、数据摘要 | 02_Life/01_健康管理 |
| `#asset` | 资产管理：支出记录、提醒、月度摘要 | 02_Life/02_资产管理 |
| `#career` | 职业发展 | 02_Life/03_职业发展 |

### lab（类别）

| 频道 | 用途 | 对应 Obsidian |
|------|------|-------------|
| `#灵感种子` | 灵感捕捉、种子碰撞 | 04_Lab/10_灵感池 |
| `#随兴实验场` | 随兴的小实验 | 04_Lab/20_实验项目 |
| `#影像实验` | 影像/摄影创意实验 | 04_Lab/20_实验项目 |
| `#视频实验` | 视频创作实验 | 04_Lab/20_实验项目 |
| `#音乐实验` | 音乐创作实验 | 04_Lab/20_实验项目 |
| ... | 新实验类型随时新增 | |

### DM 私聊

| 对象 | 用途 | 为什么不用频道 |
|------|------|-------------|
| **Partner** | 战略对话、Brief 输出、方向讨论 | 深度一对一对话，内容涉及战略判断，不适合公开 |
| **Ally** | 内省对话、日记触发、情感解读、认知引导 | 最私密的对话场景，频道会暴露不该公开的内容 |

---

## 频道权限矩阵

| 类别 | 频道 | 可写 Agent | 可读 Agent |
|------|------|-----------|-----------|
| **情报中心** | #radar-log | Radar | Partner |
| | 各 intel 论坛 | Radar | Partner, Workshop |
| **engine** | #cubox | Radar（建议入库） | — |
| | #learning | Partner, Ally | — |
| | #method | Partner, Keeper | Workshop（取弹药） |
| | #writing | Workshop, Keeper | — |
| **work-品牌** | 各业务频道 | Workshop, Keeper | Partner（只读上下文） |
| **life** | #periodic | Butler（周报推送） | Partner（月记/年记模式识别） |
| | #health | Butler | Ally（只读理解上下文） |
| | #asset | Butler | — |
| | #career | — | Ally（只读理解职业状态） |
| **lab** | #灵感种子 | Ally | Partner（碰撞建议） |
| | 各实验频道 | Workshop | Partner（方向评估）, Keeper（沉淀审核） |
| **DM** | Partner 私聊 | Partner | — |
| | Ally 私聊 | Ally | — |

---

## 与旧架构的对比

| 旧架构（按 agent 1:1） | 新架构（按场景） |
|----------------------|----------------|
| `#radar` `#partner` `#workshop` `#keeper` `#butler` `#ally` `#general` | 情报中心 / engine / work-品牌 / life / lab + DM 私聊 |
| 找 agent → 去它的频道 | 做什么事 → 去对应场景的频道 |
| Partner 和 Ally 的深度对话暴露在频道里 | Partner 和 Ally 走 DM，天然私密 |
| 频道数量固定 | 频道随业务自然增长 |

---

## 注意事项

- 各 agent 的 TOOLS.md / AGENTS.md / ROUTING.md 中仍有旧频道名引用（`#partner`、`#butler` 等），待频道架构在实际使用中稳定后再批量更新
- 新品牌上线时，在 Discord 创建新的 work-品牌名 类别即可
- 新实验类型启动时，在 lab 类别下新增频道即可

---

_此文档描述 Discord 频道的目标架构，与 Obsidian 仓库板块一一对应。_
