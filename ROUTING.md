# ROUTING.md — AI 团队协作路由规则

> 谁把什么传给谁？在哪个频道发生？这份文件定义信息流。

---

## 平台分工

| 平台 | 用途 | Agent |
|------|------|-------|
| **Discord** | 全部 agent 交互（工作 + 生活） | Radar / Partner / Workshop / Keeper / Butler |
| **飞书** | 辅助（权限理顺后可承接 Butler） | 暂无 |
| **本地命令行** | 深度对话、长任务执行 | Partner / Workshop |

当前阶段统一在 Discord。飞书权限理顺后，可评估是否将 Butler 迁移到飞书实现平台级隔离。

---

## Discord 频道结构

| 频道 | 用途 | 谁写 | 谁读 |
|------|------|------|------|
| `#radar` | 信息简报 + 即时警报 | Radar | 亚臣、Partner（参考用） |
| `#partner` | 战略对话 + Brief 输出 | Partner + 亚臣 | 亚臣 |
| `#workshop` | 任务接收 + 进度汇报 + 交付 | Workshop | 亚臣 |
| `#keeper` | 审核报告 | Keeper | 亚臣 |
| `#butler` | 生活管理（日程/健康/财务） | Butler | 亚臣 |
| `#general` | 亚臣的自由空间 | 亚臣 | 所有 agent（被动） |

---

## 信息流规则

### 主流程

```
Radar → #radar → 亚臣看到信号
                      ↓
           亚臣决定是否行动
                      ↓
       亚臣 + Partner → #partner → 对话 → Brief
                      ↓
           亚臣确认 Brief
                      ↓
       亚臣把 Brief 发到 #workshop → Workshop 执行
                      ↓
       Workshop 在关键节点暂停 → #workshop → 亚臣确认
                      ↓
       Workshop 完成 → 交付物发到 #workshop
                      ↓
       亚臣触发审核 → Keeper 在 #keeper 输出报告
                      ↓
       🟢 通过 → 亚臣拿到成品
       🔴 不通过 → 按打回路径处理
```

### 打回路径

| 问题类型 | 打回目标 | 频道 |
|---------|---------|------|
| 执行层（文案措辞、数据错误） | Workshop 重做 | `#workshop` |
| 方向层（brief 本身有矛盾） | 亚臣 + Partner 重新讨论 | `#partner` |

### 快捷路径（跳过某些环节）

| 场景 | 可跳过 | 条件 |
|------|--------|------|
| 简单任务（改个文案、调个格式） | Partner | 亚臣直接给 Workshop 下 brief |
| 低风险内容（内部文档、草稿） | Keeper | 亚臣自行判断无需审核 |
| 纯探索（头脑风暴、方向讨论） | Workshop + Keeper | 只在 Partner 频道对话 |

---

## Agent 间通信规则

### 禁止直接通信
- Agent 之间**不直接发消息**
- 所有跨 agent 信息通过**亚臣转发**或**共享知识库**传递

### 例外
- **Partner 可只读访问 `#radar` 频道历史消息**，作为对话参考素材（不发消息、不指挥 Radar）
- **Partner 可在亚臣明确指示下将 brief 发到 `#workshop`**（传话权，非调度权）

### 共享知识库
- **载体：** Obsidian Vault
- **所有工作 agent 可读**
- **写入权限：**

| Agent | 可写入 |
|-------|--------|
| Radar | 竞品档案 |
| Partner | 战略决策记录 |
| Workshop | 交付物存档、项目文档 |
| Keeper | 审核记录、规则库更新 |
| Butler | 不参与 |

### Butler 隔离
- Butler 只在 `#butler` 频道活动，不读写其他工作频道
- 工作 agent 不读写 `#butler` 频道
- Butler 不读写 Obsidian Vault
- Butler 不与任何工作 agent 有信息交集
- 隔离通过频道边界实现；未来飞书权限就绪后可升级为平台级隔离

---

## 演化规则

### 当前阶段：人工路由
- 亚臣是唯一的路由器
- 所有 agent 间的信息传递由亚臣手动完成

### 未来阶段：半自动路由（条件满足后启用）
- **条件：** 某个流程已经跑过 10 次以上，pattern 稳定
- **方式：** Partner 可以在亚臣确认后直接把 brief 推到 `#workshop`
- **约束：** 自动路由只适用于标准化流程，非标流程永远人工

### 永不自动化
- Keeper 的否决 → 永远推送给亚臣，不自动打回
- 对外发布的最终确认 → 永远由亚臣手动操作
- 新增/修改品牌核心规范 → 永远需要亚臣亲自确认

---

_这份文件由亚臣维护。Agent 不修改此文件。_
