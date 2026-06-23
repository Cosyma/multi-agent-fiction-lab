# Role-Division Patch — corrects original协议's boundaries

> Originally written by the prose-writing AI as a self-correction memo.
> **Sanitized version** — character-voice samples and chapter-specific scene cues abstracted to placeholders.

---

## 为什么补

原协议偏向"reviewer AI 给骨架，writer AI 写正文，reviewer AI 审稿"。实际工作里 author 需要更细的分工：

- **Reviewer AI 的强项**：骨架 / 伏笔 / 关键刀口台词 / 章节推进
- **Writer AI 的强项**：正文血肉 / 身体细节 / 阅读愉悦感 / 口味校准
- **Author**：最终作者，所有结论以 author 当场判断为准

所以 writer 的目标**不是骨架扩写**——是：**保留关键骨架和刀口台词，重新长出小说的肉身**。

---

## 更新后的分工

### Reviewer AI

- 给章节骨架、伏笔回收、情节点顺序
- 提供关键台词，尤其是已经很准的短句和"撞点"
- 标明章节红线：不能提前揭什么、CP 梯度到哪里
- 如果对正文口味、身体边界、引路卡有疑问，可以在对应章节目录写 `问题_给writer.md`

### Writer AI

- 对外署名：**[fixed persona name]**（不暴露背后模型）
- 写或重写正文，不做机械扩写
- 把每章骨架改成可读小说场面：动作 / 受力 / 呼吸 / 皮肤 / 物件 / 视角节奏
- 可保留 reviewer 关键台词，但旁白、身体描写、转场不能照抄"标注腔"
- 给每章建立或修订"引路卡"，帮助正文避开泛用设定卡
- 读 reviewer 稿后判断"对不对味"，给可执行反馈

### Author

- 拍板口味
- **可以直接越过协议**，让任一方写 / 改 / 停

---

## 关键原则

### 1. 台词用钉子，正文长血肉

可以保留 reviewer 的关键台词（如关系撞点 / 情节转折 / 角色 voice 极致句）——这些是"钉子"。

但**不要照抄"标注腔"旁白**——reviewer 在骨架阶段为了精准而使用的描述性短语（"很稳" / "不重" / "不落" 类）只能偶尔自然出现，不能成为正文骨架。

### 2. 不破禁区，不等于没有身体

每个项目定义自己的"禁区"——通常包括：不提前写某些 explicit content / 不在指定章节前完成某些关系动作。

但禁区之外**身体描写必须写足**——具体身体部位 + 状态变化（呼吸 / 汗 / 颜色 / 流血 / 抓痕 / 皮肤温度 / 喉间 / 腿 / 脉 / 眼 等）。

**重点**：身体必须服务关系动作，**不是单独堆感官词**。

### 3. 每章控制味必须变化

不要每章都写成同一个 dynamic（如"占有 / 私藏"循环）。每章要定义**具体的、独立的控制 maneuver**：

- 例：Ch_N 剥离 / 第一次主动碰 / 物件认领
- 例：Ch_M 等待 / 不能行动 / 边界变化
- 例：Ch_X 还回 / 解除失败 / 处置权移交
- 例：Ch_Y 绑定具象化 / 共担成实物

每章单独立引路卡，**不复用上一章**。

---

## 反向提问协议（Reviewer → Writer）

如果 reviewer 需要问 writer：

1. 在对应章节目录创建 `问题_给writer.md`
2. 写清楚问题类型：`口味 / 设定 / CP 边界 / 身体细节 / 台词保留 / 合稿判断`
3. Writer 回复放到 `_通讯/writer to reviewer/`，命名 `ChXX_writer 回复_主题.md`
4. 如果问题影响总规则，writer 同步更新 `_自用记忆.md` 或本文件

反向（writer → reviewer）沿用原握手协议里的 `问题.md`。

---

## 审稿标准补充

Reviewer 审 writer 正文时，除了原本 A/B/C 分级，再加：

- **台词刀口是否保留**：关键撞点不能被润成软话
- **正文是否摆脱骨架腔**：如果像"骨架扩写"，**即使情节点全对，也要退回重写**

Writer 审 reviewer 稿时，重点看：

- 是否有阅读愉悦感
- 身体是否写到边缘但没越界
- 旁白是否像人话，而不是规则说明

---

## 适用条件

本 patch 适用于：

- Author 已经发现"reviewer 主导骨架 + 简单扩写"出来的稿不够"对味"
- Writer AI 能力足够生成有阅读愉悦感的 prose（不是单纯的填充）
- 项目有"工艺味道"层面的精细要求（非通用 content generation）

**不适用**：
- 单 agent 自动化场景
- 不要求 author 终审的 production pipeline
- 短篇 / 流式内容生成

---

## 学术对照

| 概念 | 学术 anchor |
|---|---|
| "钉子 vs 血肉" 分工 | Schön (1983) reflective practitioner — practice 不能被 articulation 全 cover |
| Reviewer 不写 / Writer 不审 | Lave & Wenger (1991) legitimate peripheral participation 的 mirror — 角色专门化提升 quality |
| 控制味每章变化 | Vary 原则（fiction craft literature 通用） |

---

*Sanitized 2026-06-23 from production deployment*
*Original artifact: 2026-06-04 self-correction memo by writer AI*
*Licensed under CC BY 4.0*
