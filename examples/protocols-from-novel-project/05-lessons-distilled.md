# Project Lessons Distilled

> 24-chapter long-form fiction project, 4 months active deployment, from outline-to-complete-draft collaboration protocol pack.
> 写给未来的小说项目——可直接复用目录结构 + SOP + 模板。
> **Sanitized version** — 角色名 / 物件 / 设定 / 章节 specifics 抽象化；架构 + 流程 + 模板保留。

---

## 一、项目背景与协作分工

**三方协作**：
- **Author**：作者本人 / 骨架 / 终审权 / 工艺红线设定者
- **Writer AI（[fixed persona name]，基于 GPT-class 模型）**：正文写作（每章分段：段1 / 段2，按大纲产出 `writer 正文.md`）
- **Reviewer AI（基于 Claude-class 模型）**：审稿 + 合稿 + 物件叙事追踪 + 跨章伏笔记账 + 项目状态维护

**核心分工原则**：
- **骨架在 author**——情节 / 红线 / 工艺方向由 author 定
- **正文在 writer**——每段产出完整正文，自由发挥但守红线
- **审稿 + 追踪在 reviewer**——双对照检查 / ABC 分级 / 跨章记账 / 合稿 / 状态更新

**最值得记的一条**：**reviewer 不写正文**。只审、只合稿、只记账。**写作权完全在 writer**。这避免了 reviewer 模型的"代笔倾向"对作者声音的污染。

---

## 二、目录结构（开新书直接复制）

```
项目根/
├── _通讯/
│   ├── Ch{NN}/
│   │   ├── 大纲.md           ← author 写，AI 只读
│   │   ├── 段1/
│   │   │   ├── writer 正文.md ← writer 产出
│   │   │   └── DONE → DONE_PROCESSED  ← 信号文件
│   │   ├── 段2/
│   │   │   └── （同上结构）
│   │   └── 合稿.md           ← reviewer 产出（段1 + 段2 合并）
│   ├── reviewer to writer/
│   │   └── Ch{NN}_段{N}_反馈.md  ← reviewer 产出（审稿反馈给 writer）
│   └── 项目状态/
│       └── 项目状态.md       ← reviewer 维护
├── 正文ing/
│   └── 项目_第{NN}章_进行中.md  ← author 的骨架原稿
└── _经验沉淀.md              ← 本文件
```

**关键文件**：
- `DONE` / `DONE_PROCESSED` —— 文件信号机制，**比通信群消息可靠**：writer 写完段 → touch `DONE`；reviewer 审完 → `mv DONE DONE_PROCESSED`。无歧义，可 grep
- `项目状态.md` —— 一张表盖住 NN 章状态（大纲 / 段1 写 / 段1 反馈 / 段2 写 / 段2 反馈 / 合稿）。Author 一眼看到全局
- `合稿.md` —— 段1 + 段2 拼回完整章节，`---` 分隔段间。Author 最终读这个文件

---

## 三、SOP（每章处理流程）

### Writer 产出段后

1. Writer 写 `Ch{NN}/段{N}/writer 正文.md`
2. Writer touch `Ch{NN}/段{N}/DONE`（信号）

### Reviewer 扫描 + 处理

```bash
# 1. 扫所有未处理的 DONE
find {项目根}/_通讯 -name "DONE" -not -name "DONE_PROCESSED"
```

发现 DONE 后：

1. **读** `Ch{NN}/大纲.md`（如果不在 context 里）+ `Ch{NN}/段{N}/writer 正文.md`
2. **审** 按"双对照 + ABC 自由发挥分级 + 红线自查"模板（见第四节）
3. **写** `reviewer to writer/Ch{NN}_段{N}_反馈.md`
4. **标处理完** `mv DONE DONE_PROCESSED`
5. **更新** `项目状态.md` 对应行
6. **段2 通过后**：合稿 `Ch{NN}/合稿.md`（段1 正文 + `---` + 段2 正文）
7. **ScheduleWakeup** 1200s 继续 polling 下一章

### Polling 节奏

- **默认**：`ScheduleWakeup 1200`（20 分钟）—— writer 写一段需要 15-30 分钟，cache 反正要 miss，长 sleep 省 token
- **不要用 300s** —— 最差选择（cache miss + sleep 太短）
- **实测**：1200s 长间隔 + 长尾偶尔有信号，writer 自然完成节奏 24 章约 5-6 小时

---

## 四、审稿模板：双对照 + ABC 分级

每段反馈固定结构（**这个模板是项目最大的工艺资产，请保留**）：

```markdown
# Ch{NN} 段{N} 反馈

## 结论
✅ 通过 → 写段{N+1} / 合稿 Ch{NN}
（最重的几笔）—— 用大引用块列 6-12 处最重的句子+一行注释

## 双对照
### A 线（骨架点）
- 大纲明定的每个情节点 + ✅/⚠️
### B 线（味道/工艺）
- 物件叙事/身体物理/对位回扣/writer 自由发挥的钉子（列详细）

## 自由发挥分级
### A 类（必删）
（writer 违反红线/破坏物件链/抒情过头的——必改）
### B 类（保留+记账）
1. Writer 自由发挥的钉子 —— 保留 —— **记账·Ch{NN+X} 时回扣**
（这是最关键的：reviewer 把 writer 的好句子记下来，要求 writer 在后续章节回扣兑现）
### C 类（不动）
（骨架点+大对话+章末停点）

## 几条 Ch{NN+1} 要带的（提醒一下）
1. 下一章必须带的钉子
2. 下一章可选的自由发挥位置

## 红线自查（reviewer）
- 视角是否守住 ✅
- 时间线是否自洽 ✅
- CP 梯度是否克制 ✅
- 未提前透的内容 ✅
- [项目特定红线 list] ✅

## 下一步
→ 明确的下一动作

reviewer
```

**ABC 分级的关键判断**：
- **A 类**：违反红线 = 必删（本项目 24 章只出现过 1 次，writer 守得极好）
- **B 类**：writer 的自由发挥是好的，但要记账——**让它在后续章节兑现**
- **C 类**：骨架点 + 对话，不能动

**B 类记账机制是项目最大的复利**：

实测的兑现 pattern（举例 sanitized）：
- Ch_X 段{N} B 类记账#1（[某 motif 暗钉]）→ Ch_{X+4} 段{M} 兑现
- Ch_X 段{N} B 类记账#3（[某身体/物件 motif]）→ Ch_{X+1} 段{M} 兑现
- Ch_Y 段{N} B 类记账#1（[某分裂/对照 motif]）→ Ch_{Y+1}/Ch_{Y+2}/Ch_{Y+4}/Ch_{Y+6} **连续 4 次兑现**
- Ch_Z 段{N} B 类记账#5（[某物件双重含义]）→ Ch_{Z+2} 段{M} 兑现

**Writer 连续 7+ 次精准兑现 B 类记账**——这是协作工艺的核心证明。

---

## 五、本书工艺红线（开新书可微调）

### 写作工艺红线

1. **抒情留白**——不崩开、不哭、不直白告白
2. **物件物理叙事比心理叙事重**——[某 object] 的位置变化比"他爱他"更重
3. **某 lore 余味只一闪不解释**——不出现 [某 explicit term]
4. **CP 物理梯度精确分级**——本书全程 8 级（具体每级因项目而异）
5. **不浪漫·是责任**（HE 工艺）——结尾落在"门要守一辈子"类承担动作
6. **不写"几年后""多年后"**——落在当下
7. **配角余波一句话收**——配角不抢戏
8. **真名留白**——某些 identity / 真名 不需要被释放

### 协作红线

1. **Reviewer 不写正文**——只审稿、合稿、记账
2. **Writer 不动大纲**——大纲在 author 手里
3. **配角命名 / 关键 lore 决策有歧义时停下问 author**
4. **红线 vs 自由发挥的分级要严格**——A 类必删、B 类记账、C 类不动

---

## 六、Writer 的合稿协议

每章大纲附带的"语感种子"指令模板：

```
> Tag：（章核心）
>
> 主种子建议（避开已用段）：
> A) 本书 Ch{XX}（reviewer 合稿） ⭐ 必看 —— （理由）
> B) （第二层 fallback：他书段）—— （理由）
>
> 推荐主种子：A ⭐ 必看 + 第二层 fallback B
>
> 记 `已用片段台账.md`
```

**关键点**：
- **每章 ≤ 6 个情节点**（writer 写不了 12 个，太散）
- **守住两条**（章特定红线，0-2 条）
- **语感种子来源去重**（避免 writer 写两章用同一种感觉）
- **字数明定**（如 "约 6000-8000 字。不要超过 8500"）
- **钉子列表给 writer**（最重的 10-20 个具体句子 / 物理动作，writer 严守不改）

---

## 七、合稿格式

```markdown
# Ch{NN} {章名}（暂）

{段1 正文，不含段标题}

---

{段2 正文，不含段标题}
```

**注意**：
- 合稿时不要带段标题，让章节读起来一气呵成
- `---` 是章中断点的视觉提示（author 审稿时知道节奏切换在哪）
- 标点符号统一（半角 → 中文全角）——writer 偶尔出半角，合稿时统一

---

## 八、项目状态.md 模板

```markdown
# {项目名} ChXX-ChYY 正文化 · 项目状态

> Reviewer 维护。每次进项目扫描所有 DONE 信号后更新。
> {Author} 一眼能看到 {NN} 章进度。

最后扫描：{date}（{本次扫描的重要事件}）

---

## 总进度

| 章 | 大纲 | 段1 写 | 段1 反馈 | 段2 写 | 段2 反馈 | 合稿 |
|---|---|---|---|---|---|---|
| Ch{NN} {章名} | ✅ | ✅ 完成 | ✅ 通过 | ✅ 完成 | ✅ 通过 | ✅ 合稿落定 ⭐ {亮点} |
| ... |

图例：✅ 完成 / ⏳ 等 writer / 🔍 等 reviewer 审 / ❓ 阻塞 / — 未到

---

## 当前待我处理（按 DONE 信号扫描结果）
（无新 DONE）/ Ch{NN} 段{N}

---

## 当前阻塞（writer 提了问题等回）
（无）

---

## Reviewer 扫描 SOP
{保留 find 命令}
```

---

## 九、最值得带走的 8 条 meta 经验

1. **多 LLM 协作要有"明确分工 + 文件信号 + 状态看板"三件套**——通过 IM 协作会丢消息、看不清全局
2. **审稿者的"B 类记账"是协作最大的复利**——把对方的好句子记下来要求后续兑现，对方就会被"工艺暗钉"训练得越来越准
3. **物件叙事链 = 跨章伏笔的物理化**——比"角色心理"更可靠的连贯性手段
4. **某些 lore 元素 / "留白"工艺**：要让 LLM 不解释、不点破，需要在大纲里**明确写出"严守不解释"+三句具体场景**，否则 LLM 默认会解释
5. **章末停点的节奏感**：每章末句 ≤ 一行，落在物理画面上（不在抒情 / 解释上收）
6. **配角余波"一句话收"**：配角不抢戏，是 HE 工艺重要的一环
7. **红线 vs 自由发挥的分级**：纯红线会让正文僵硬，纯自由会让正文散——A/B/C 三级（必删 / 记账 / 不动）是最好的平衡
8. **"克制即重量"**：CP 真正的破点用最少的物理细节实现——比任何 explicit 描写都重

---

## 十、复用清单（开新书时的 checklist）

- [ ] 创建目录结构（第二节）
- [ ] 写第一章大纲（author）
- [ ] 定本书的"工艺红线"列表（第五节模板，按本书调）
- [ ] 设 CP 物理梯度（每一级 + 出现的章节）
- [ ] 设三大物件（每个物件出现章节 + 最终归宿）
- [ ] 定章首 / 章末节奏规则
- [ ] 写一份"给 writer 的合稿协议"（第六节模板）
- [ ] 初始化项目状态.md（第八节模板）
- [ ] 第一章产出后：reviewer 用本文件第四节模板做反馈
- [ ] 后续章节按 SOP 跑

---

## 学术对照（澜补的）

| 概念 | 学术 anchor |
|---|---|
| 文件信号机制 | Schmidt & Bannon (1992) articulation work / Star (1989) boundary objects |
| B 类记账机制 | Bechky (2003) "Object lessons" — tangible objects as cross-team coordination resources |
| ABC 分级（必删 / 记账 / 不动）| Brown, Malveau et al. (1998) *AntiPatterns* + Donald Murray "voice" hierarchy |
| 三方分工铁律 | Lave & Wenger (1991) legitimate peripheral participation |
| 1200s polling 节奏 | matches transformer cache window architecture（5-min cache vs sleep cost trade-off）|

---

*Sanitized 2026-06-23 from production deployment (24-chapter long-form fiction, 4 months)*
*Original: reviewer AI's self-distilled experience pack, written at project close*
*Licensed under CC BY 4.0*
