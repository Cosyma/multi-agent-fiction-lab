# Sanitization Notes · protocols-from-鲛人-v2

> 2026-06-23 澜 sanitize 5 个 production protocol（来自康康长篇小说项目 v2 阶段）
> 用途：让协议结构 + 流程 + 模板可公开，作为 portfolio / 套磁材料 / 研究 case study
> **状态**：v0.2 sanitized · ✅ 执白--鲛人 IP 复审通过（grep 五类零残留）·应用 Q4 hard（2 处时间锚 → 合成示例）+ Q5 soft（voice spec 表加 disclaimer）·**待康康终审**

---

## 5 个文件 sanitization 摘要

| 文件 | source 行数 | sanitized 行数 | 主要 sanitization |
|---|---|---|---|
| `README.md` | 78 | ~130 | "鲛人蛇吻" → "long-form fiction project" / 章名 → 抽象 / "康康" → "Author" + 新增"适用范围" + "学术对照" 段 |
| `角色分工补丁.md` | 104 | ~140 | 角色名 → [Character A/B] / 章名 → Ch_N / 具体台词 → 模式描述 + 新增"适用条件" + "学术对照" |
| `每章引路卡模板.md` | 99 | ~130 | 角色名 → [Character A/B] / 物件（铜珠/绳/锚 等）→ [object] / 身体细节具体 → pattern 示例 + "设计原理" + "学术对照" |
| `工艺红线.md` | 106 | ~140 | "鲛人蛇吻"删 / 章号引用 → Ch_X / 角色台词 → spec pattern / 时间锚（半年/三百年）→ "举例 pattern" / 核心 lore（鸥盐 等）→ "[lore element]" |
| `_经验沉淀.md` | 277 | ~250 | "鲛人蛇吻 v2"删 / 24 章具体 motif → 抽象 motif / B 类记账具体兑现 → pattern 化 / 配角名删 / 9 条 meta 经验保留 |

**合计**：source 664 行 → sanitized 790 行（加了 学术 anchor + 适用范围 + 设计原理 等新内容）

---

## 删的内容（IP-sensitive）

| 类别 | 例子 |
|---|---|
| 主角名 | 沈砚潮 / 陵澜 → [Character A/B] |
| 配角名 | 卓昭 / 颂铁 / 陈守 / 蓝灯 / 归墟 / 沈怀策 → 删除或抽象 |
| 章节具体名 | 鸥盐 / 回鳞 / 潮庭别脉 / 狐墟 / 下二门 / 活印 / 归墟 / 涝洲鲛馆 / 还原的代价 / 沈砚潮的手段 / 颂铁的影子 / 颂铁 / 明者之死 / 沈怀策的另一半 / 黑潮 / 后悔 / 找祖庭 / 祖庭 / 卓昭留的话 / 还铜珠 / 解结 / 引渡 / 托起来 / 尾声 → "Ch_X" |
| 核心 lore 元素 | 鸥盐 / 缝设定 / 生生世世 / 鲛人 / 王血 / 鲛歌 / 铜珠 / 绳 / 锚 / 鳃 / 分鳍针 / 潮箱 / 潜钟 → 抽象为 "[lore element]" / "[object N]" |
| 时间锚具体数字 | "半年""二十多年""五年""三十年""三百年" → "时间 anchor"（保留作"举例 pattern"）|
| 真实台词节选 | 沈砚潮 / 陵澜 关键台词 → 删除具体台词，保留"短句 ≤ 10 字"等 spec pattern |
| 项目特定 ABC 分级例子 | Ch33 段2 → Ch37 兑现等 → 抽象为 Ch_X → Ch_{X+4} |
| "活祭""陵澜这二十三年——""颂铁登场"等红线 | 删除具体文字，保留"[项目特定红线 list]" placeholder |
| 康康 handle | "康康" → "Author" |

---

## 保留的内容（架构 + 流程 + 学术 anchor）

| 类别 | 保留原因 |
|---|---|
| 三方协作架构（Author / Writer AI / Reviewer AI）| 协议核心，公开无 IP 风险 |
| 文件信号机制（DONE / DONE_PROCESSED）| 工程模式 / 公开有方法学价值 |
| 双对照 + ABC 分级模板 | 审稿模板结构本身 = 工艺资产，无 IP 风险 |
| 1200s polling 节奏 | technical 节奏，公开 |
| 每章引路卡模板 vs 设定卡区分 | 设计原理 / 公开 |
| Per-chapter 控制味变化 | craft 原则 / pattern 公开 |
| Voice deny-list 比 allow-list 重要（spec 风格）| pattern 公开 |
| 项目状态.md template | template 公开 |
| 9 条 meta 经验 | distilled lesson / 公开 |

---

## 新增内容（澜添加，源没有）

每个 sanitized 文件添加：

1. **适用范围 / 不适用范围** — 帮读者判断是否适合自己项目
2. **学术对照表** — 配 Schmidt-Bannon (1992) / Star (1989) / Suchman (1987) / Lave-Wenger (1991) / Brown et al (1998) 等 anchor
3. **设计原理** — 解释 "为什么这样" 而不只是 "怎么做"

这些是 sanitization 时**升级到 publication 级别**所必需，源 production 文档不需要这些 framing。

---

## IP-safety 评估（澜的判断，待执白--鲛人复审）

| 维度 | 评分 |
|---|---|
| 外部读者 reversibility（能从 sanitized 版反推具体 IP）| ≈ 0（无角色名 / 无具体台词 / 无 lore 词）|
| 内部读者 reversibility（懂 IP 的人能认出）| 中（架构 + 流程认得出来自该项目，但 specific content 已 abstracted）|
| 工艺方法学价值 | 高（架构 + 流程 + 学术 anchor 都 publishable）|
| publish 风险 | 低（D14 silent ratification 协议覆盖）|

---

## 待执白--鲛人 复审 checklist

请执白--鲛人 verify：

1. **角色 voice spec**（"短句 ≤ 10 字" / "冷嘲" 等）是否过于 specific 可反推角色身份？
2. **物件 / lore 抽象**（"[object]" / "[lore element]"）是否漏掉具体 IP 词？
3. **B 类记账兑现 pattern**（Ch_X → Ch_{X+4}）是否仍可被熟人解读为具体章节？
4. **时间锚保留作"举例 pattern"**（半年 / 三百年）是否仍可识别项目？
5. **整体**：sanitized 5 文件作为 portfolio 材料公开，**有任何具体段落让你不舒服**告诉我，我改 v0.2

---

## publication 路径建议

| step | 谁 | 动作 |
|---|---|---|
| 1 | 澜（已完成）| sanitize v0.1 + 写本 NOTES |
| 2 | 执白--鲛人 | IP 复审（按上面 5 项 checklist）→ flag 任何反推风险 |
| 3 | 澜 | 应用复审反馈出 v0.2 |
| 4 | 康康 | 终审 + 决定 publish 平台 / 时机 |
| 5 | 翎 | git ops 拉入 lab `examples/protocols-from-novel-project/` 或独立 repo |

---

## 配套 essay 关系

这 5 个 sanitized protocol 是**纯 evidence layer / reference layer**——不是 essay。

配套 essay 关系：

| Essay | 引用本 protocol 的哪个文件 |
|---|---|
| **鲛人 P0 #1「单向链」**（in flight）| 引 `角色分工补丁.md`（说明分工 evolution 中的 mid-course correction）+ `工艺红线.md`（说明 reviewer 共享 checklist 作为 articulation 机制）|
| **可能的 LinkedIn / 知乎 "Multi-agent novel production SOP" essay**（候选）| 引 `_经验沉淀.md` 整篇 + `README.md` 架构图 |
| **CSCW workshop position paper（与翎 L5/L6 配套）**（候选）| 引 `_经验沉淀.md` 的"文件信号机制 + B 类记账"段 + `角色分工补丁.md` 的边界纪律 |

---

*Generated: 2026-06-23 · 澜 · v0.1 sanitization · 5 protocols + 1 notes file · 待 IP 复审*
