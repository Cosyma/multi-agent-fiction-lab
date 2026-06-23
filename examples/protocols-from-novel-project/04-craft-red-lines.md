# Craft Red Lines — for the writer AI

> 长篇正文工艺铁律。Reviewer AI 按这些校对。
> **Sanitized version** — 项目特定的世界设定 / 角色名 / 时间锚 / lore 抽象化；红线结构 + 自查机制 + 角色 voice spec 模式保留。

---

## 六条铁律（保留架构，举例 sanitize）

### 1. 情感引擎

每章必须有：困境是无解的 → 角色用具体动作承担 → 留白让读者感觉到。

不及格信号：读完一章没"被压住"的瞬间。

### 2. 物理逻辑过关

- 任何**数字 / 时间 / 人物** → **回原文确认**，不凭手感
- 比喻的主体真做得到吗（举例：人活不了 300 年别说"找 300 年"——这是 author 戳过 reviewer 的 bug pattern）
- 不及格信号：author 一句话能戳穿

### 3. 主体性

- 角色**自己算 / 自己选 / 自己长出转折**
- 不是作者推角色去做某事
- 不及格信号：感觉作者在推动剧情

### 4. CP 张力——分类（关键！）

- **单向控制 / 虐场**（如 [project-specific scene types]）
  → **感官化是底色，保留**（"一线冰火"等强感官写法**要的**）
- **双向情爱**（如 CP 之间的接吻 / 亲密）
  → 守"**不肯说出口**"的张力，**克制**

### 5. 视角纪律（见下方专章）

### 6. 不要做的（见下方 grep 清单）

---

## 视角

- **第三人称限知**，主要在 **[Character A] + [Character B]** 之间切换
- 一个场景跟 **一个**主视角（不能同时进两人内心）
- 切换发生在**章 / 段落边界**，明确
- **配角不进内心** — 只通过动作 + 对话 + 别人对他的观察来塑造
- **Narrator 可以有声音** — 做 judgment、章末给"达成"的一句、点破当下 meaning。但**克制**，不解释逻辑、不抒情

| 谁 | 有独白 / 内心想法 |
|---|---|
| [Character A] | ✅ 主视角时 |
| [Character B] | ✅ 主视角时 |
| 配角 | ❌（动作 + 对话） |
| Narrator | ⚠️ 偶尔，克制 |

---

## 不要做的（自查 grep）

| 不要 | 例 |
|---|---|
| ❌ 大纲编号写进正文 | D17 / D19 / D29 等内部编号 |
| ❌ "X 没说话 / X 沉默了" | 用每个角色独属物理动作代替 |
| ❌ 作者视角穿帮 | "意味着" / "实际上" / "真相是" / "似乎正" |
| ❌ 抖底牌 | 主角不该知道的信息别让他说 |
| ❌ 完整 [某 lore 元素的释放] | 只在指定章节出现，别处只许半截 / 短鸣 |

---

## 角色台词风格（pattern 示例）

> *Voice spec 是工艺示例——参数为某具体项目的内部值。读者应替换为自己项目实际 voice 字数与 affect 类别。这里的具体性（"≤ 10 字" / "12-30 字" / "嘲讽 / 反咬" 等）是为了展示 spec 该写到什么颗粒度，不是 universal 规则。*

### Character A（举例 spec）

- **≤ 10 字最常见**，平声短句
- 命令 / 决定 / 事实陈述，**不解释**
- 例："嗯""会""走""下去""上来""我数三声""不要了"
- **不会**：抒情 / 大笑（最大表情 = 眼神微沉 / 抬眉）/ 解释判断逻辑 / 主动哄对方 / 长句（>20 字警惕）

### Character B（举例 spec）

- **中-长 12-30 字常见**，冷 / 嘲 / 刺
- 嘲讽 / 反咬 / 给一半信息 / 拐弯认输
- **不会**：直白求饶 / 完整 [lore-specific vocal element] / 主动靠近对方（被动）/ 用 [某种 affect display] 表情 / 主动承认对方对他重要

### 配角

- 见各项目独立的 character brief
- 部分配角有独立 voice，部分是工具人

→ **关键**：每个角色的"不会"清单比"会"清单更重要。voice 是 deny-list 出来的。

---

## 时间线（铁约束）

每个项目维护自己的时间线 source-of-truth 文件（如 `时间线_圆坑.md`）。

铁规：
- 关键时间锚（如"几个月前""二十年级跨度""数百年级跨度"等多层时间叠加）照 source-of-truth 走
- **不允许凭手感发挥**时间数字
- 任何回忆 / 闪回都先回 source-of-truth 确认

> *Note: 上面是合成示例。实际项目的时间锚由作者 source-of-truth 定，具体数字因项目而异。*

---

## 核心 lore 元素（如该项目有）

每个项目通常有 1-2 个核心 lore 元素（举例 pattern）：
- 某 sensory element（保留"味"，不写物理形态）
- 某 visual element（保留某种描述定式）
- 某 cyclical element（只在指定章节出现）

→ **铁规**：不在指定章节别埋 / 别提前透 / 别完整释放。

---

## 写完前自查（reviewer 也按此清单审）

Writer 写完一章正文，发给 reviewer 前先过一遍：

- [ ] 情感引擎 6 条：困境无解？承担动作短句？留白？
- [ ] 物理逻辑：数字 / 时间 / 人物回原文查过？
- [ ] 主体性：角色自己长还是被推？
- [ ] grep "不是.{1,15}是" = 0？（"不是 X 是 X" anti-pattern）
- [ ] grep "D[0-9]" = 0？（大纲编号未漏到正文）
- [ ] [Character A] 没说 >20 字的长句？
- [ ] [Character B] 没用 [forbidden affect display] / 没主动告白？
- [ ] [核心 lore 元素] 没在禁区出现？

Reviewer 会按这个清单审稿。哪条不过，反馈里点出来。

---

## 学术对照

| 概念 | 学术 anchor |
|---|---|
| 铁律 + 自查 grep 清单 | Brown, Malveau et al. (1998) *AntiPatterns* — 反模式 catalog 是 craft 传承的关键载体 |
| Voice deny-list 比 allow-list 重要 | Stephen King *On Writing* + Donald Murray on "voice" — 角色 voice 是通过禁止某些表达定义的 |
| Reviewer 按相同 checklist 审 | Schmidt & Bannon (1992) articulation work — 共享 checklist 作为协调机制 |

---

*Sanitized 2026-06-23 from production deployment*
*Licensed under CC BY 4.0*
