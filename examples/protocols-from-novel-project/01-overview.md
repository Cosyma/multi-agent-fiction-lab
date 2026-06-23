# Multi-Agent Novel Production Workspace — Protocol

> Production protocol from a 24-chapter long-form fiction project (~4 months active deployment).
> **Sanitized version** — character names, world-setting lore, and chapter titles abstracted to placeholders. The collaboration structure, file-signal mechanics, and process discipline preserved.
> Original artifact resides in author's private project tree; this is the public methodology summary.

---

## 三角色协作（3-way collaboration）

| Role | Owner | 职责 |
|---|---|---|
| **Author** | 人类作者 | 统筹 / 最终审美权 / 工艺红线 / 骨架 |
| **执白（CC = Claude Code 实例）** | AI agent | 守骨架 / 方法论 / 味道 / 审稿 / 合稿 / 跨章追踪 / 项目状态维护 |
| **烨（GPT 实例）** | AI agent | 正文血肉 / 身体细节 / 阅读愉悦感 / 口味校准 |

**关键边界**：**执白不写正文**——避免审稿模型代笔污染作者声音。烨不审稿——避免写者既写又审。

---

## 协作流程

### 必读 stack（agent 启动协议）

按顺序读：
1. `执白 to G/握手协议.md` — 完整流程 + 反馈格式
2. `工艺红线.md` — 6 条铁律
3. `角色分工补丁.md` — 修正后的边界（必看）
4. `每章引路卡模板.md` — 每章不复用同一张设定卡
5. 当前章的 `ChXX/大纲.md`

### 写作循环

```
Author 给章节骨架 + 引路卡
       ↓
烨 写 ChXX/段{N}/{agent}_正文.md
烨 touch ChXX/段{N}/DONE  ← 空文件 = 完成信号
       ↓
执白 扫 find . -name DONE -not -name DONE_PROCESSED
执白 审稿 → 写 ChXX/段{N}/执白反馈.md
执白 mv DONE DONE_PROCESSED  ← 状态切换
       ↓
烨 看反馈 → 必要时改 → 新 DONE
       ↓
执白 合稿 → 跨章追踪 → 总台账更新
       ↓
Author 终审
```

### 总台账机制

`项目状态/项目状态.md` 由执白维护，作者一眼能看到 24 章进度（骨架 / 参考正文 / 当前正文 / 审稿状态四列）。

---

## 配套设定文档（每章必查 stack）

| 文档 | 作用 |
|---|---|
| `时间线_圆坑.md` | 全书时间线（防止时间漂移）+ 关键设定锚点 |
| `设定卡_v{N}.md` | 主角档 + 世界空间分区 |
| `系列说明.md` | 跨季 / 跨卷 / 跨项目关系 |
| `_工作室/接手计划.md` | 当前阶段接手计划 |
| **已落稿正文** | 原文权威——任何数字 / 时间 / 人物**先回这里查**，不凭手感 |

---

## GPT 自用工作室

`_GPT工作室/` 存 GPT 自己的"口味记忆 / 正文需求盘点 / 后续审稿经验"。

**不进正式协议**——避免把过程性判断污染对外 spec。

---

## 项目级铁规（每个项目自定）

> 这一段对外不能照搬，只展示**该层有铁规**这件事。每个项目的铁规由作者定，与本协议解耦。

举例（脱敏后的 pattern）：
- 已落稿章节**不动**——已是作者正文
- 关键时间锚（如"几个月级跨度""二十年级跨度""数百年级跨度"等多层时间叠加）照某一份 source-of-truth 走，不允许凭手感发挥
- 某些核心 craft 元素（"味"层，不写物理形态）写法约定
- 某些 lore 元素（如"轮回 / 生生世世"）只在指定章节出现，**别处不许埋**
- 各角色 voice 约定（短句 / 冷嘲 / 工具人）

---

## 适用范围

本协议适用于：

- 单作者 + 1-2 个 AI 协作者的长篇创作
- 章节级别有明确边界（不适用流式 / 实时协作）
- 作者愿意承担最终审美权（不适用作者放手让 AI 自治）
- 项目寿命 > 1 月（短期 task 不值得这套协议开销）

**不适用**：
- 多人作者协作（本协议假设单一 author 终审）
- AI agent 数量 > 3（>3 时文件信号开销 > 收益）
- 实时协作场景（DONE 文件机制需要轮询 cycle）

---

## 学术对照

| 概念 | 学术 anchor |
|---|---|
| 文件信号机制（DONE / DONE_PROCESSED） | Schmidt & Bannon (1992) articulation work + Star (1989) boundary objects |
| 角色硬边界（执白不写正文 / 烨不审稿） | Lave & Wenger (1991) division of legitimate participation |
| 引路卡不复用 | situated action（Suchman 1987）— plans-as-resources not plans-as-prescriptions |

---

*Sanitized 2026-06-23 from production deployment*
*Original artifact: 4 months active use, 24 chapters output*
*Licensed under CC BY 4.0*
