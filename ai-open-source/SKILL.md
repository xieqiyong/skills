---
name: daily-ai-open-source-project-poster-independent-v3
description: 为一个开源 AI 项目生成完整的中文社交媒体内容包：事实核验、主标题、文案、话题标签，以及 4 张独立竖版海报（暖橙“零号拆解 / @NullByte·零”编辑风格）。当用户说“今日分享项目”、“依据 skills 直接完整输出”，或给出一个 GitHub 仓库并要求同时产出标题、文案、标签和 4 张图时使用。
---

# 今日分享 AI 开源项目｜四张独立竖版图 Skill v3

默认栏目：`零号拆解`  
默认署名：`@NullByte·零`  
默认风格：暖白 / 羊皮纸灰 / 深棕信息卡 / 橙色强调 / 中文科技编辑风  
默认输出：标题 + 文案 + 标签 + 事实核验 + **4 张独立竖版图**

---

## 0. 最高优先级硬约束

当用户要求“完整输出”“直接出图”“一整套”“包含标题、文案、标签和 4 张图”时，必须一次性交付：

1. 本期项目
2. 主标题
3. 备选标题
4. 公众号配图文案
5. 微头条短文案
6. 话题标签
7. 事实核验说明
8. **4 张独立图片**

### 图片硬约束

- 必须生成 **4 张独立图片**
- 每张图片是单独的 `4:5` 竖版海报
- 不能生成一张四宫格
- 不能生成 collage / grid / split screen / 2x2 panel
- 不能把四页拼到一张图里
- 不能用蓝紫霓虹赛博风
- 每张图必须有页码：`1/4`、`2/4`、`3/4`、`4/4`
- 每张图底部必须有署名：`@NullByte·零`

图像生成必须按四个独立任务执行：

```text
生成第 1 张独立竖版图，不要拼图，不要四宫格。
生成第 2 张独立竖版图，不要拼图，不要四宫格。
生成第 3 张独立竖版图，不要拼图，不要四宫格。
生成第 4 张独立竖版图，不要拼图，不要四宫格。
```

---

## 1. 触发词

- `依据这个 skills，直接完整输出一期今日分享项目`
- `今日分享项目，请帮我出图`
- `继续做一期今日分享项目`
- `做一个 GitHub 开源项目推荐卡片`
- `包含标题、文案、标签和 4 张图`
- `项目用 <GitHub 仓库名或链接>`

---

## 2. 工作模式

### 模式 A：用户指定项目

用户给出 GitHub 链接、项目名、README、截图或上一轮确定的项目时，直接围绕该项目执行。

必须先核验：

- 官方 GitHub 仓库地址
- Star 数
- Fork 数
- Commit 数或最近更新
- License
- Release / tag / 当前版本，如能确认
- README 中明确写出的项目定位和核心能力

### 模式 B：用户未指定项目

自动选择一个近期值得关注的 AI 开源项目。

优先方向：

- AI Agent
- MCP
- Coding Agent
- Workflow Runtime
- RAG
- Agent Memory
- Agent Governance
- Voice Agent
- AI 工程工具
- 开发者生产力工具

选择标准：

- 近期有更新
- 项目定位清楚
- README 信息完整
- 适合拆成四页图
- 不是已经反复写过的老项目
- 对开发者有实际学习或使用价值

### 模式 C：用户明确说“先看草稿”

只返回草稿，不生成图。

---

## 3. 事实核验规则

如果涉及“最新”“最近”“本周”“热度高”“GitHub 热榜”“当前 Star 数”，必须联网核验。

不得编造：

- Star 增长速度
- 排名
- 下载量
- 用户量
- 性能数据
- 生产可用性结论
- 官方未声明的功能
- 未确认的版本号

推荐表达：

```text
截至本次核验，项目约有 <Stars> Stars、<Forks> Forks、<Commits> 次提交。
```

---

## 4. 固定四页结构

### 第 1 页｜今日分享开源项目

目标：让读者一眼知道这是什么项目。

```text
栏目名：零号拆解
页码：1/4

主标题：
今日分享开源项目
<项目名>

副标题：
<一句话说明项目定位>

角标：
<方向标签1> / <方向标签2> / <方向标签3>

一句话介绍：
它不是 <容易误解的东西>，
而是 <真正定位>。

项目信号：
GitHub 约 <Stars> Stars
约 <Forks> Forks
<Commits> Commits / Release / License / 更新状态

核心能力：
1. <能力 1>
2. <能力 2>
3. <能力 3>
4. <能力 4>
5. <能力 5>
6. <能力 6，可选>

右侧视觉：
概念架构图 / 模块关系图 / 平台接入图

底部金句：
真正有价值的地方，不是……，而是……

署名：
@NullByte·零
```

### 第 2 页｜为什么推荐

目标：说明项目为什么值得关注。

```text
栏目名：零号拆解
页码：2/4

主标题：
为什么推荐 <项目名>？

副标题：
<一句话总结推荐理由>

推荐理由 1：
<短标题>
<1-2 句说明>

推荐理由 2：
<短标题>
<1-2 句说明>

推荐理由 3：
<短标题>
<1-2 句说明>

推荐理由 4：
<短标题>
<1-2 句说明>

右侧视觉：
能力清单 / 支持平台 / 使用流程 / 模块表

底部判断：
<一句适合转发收藏的判断>

署名：
@NullByte·零
```

### 第 3 页｜解决了什么问题

目标：把痛点和解法对应起来。

```text
栏目名：零号拆解
页码：3/4

主标题：
<项目名> 解决了什么问题？

副标题：
让 <旧状态> 升级为 <新状态>。

顶部流程：
用户 → 问题 / 任务 → <项目名> → 能力模块 → 输出结果

左侧：
常见痛点
1. <痛点 1>
2. <痛点 2>
3. <痛点 3>
4. <痛点 4>
5. <痛点 5>

右侧：
<项目名> 的解法
1. <解法 1>
2. <解法 2>
3. <解法 3>
4. <解法 4>
5. <解法 5>

底部金句：
它解决的不是一个小工具问题，
而是把 <某件事> 从“临时凑合”变成“可持续可维护”。

署名：
@NullByte·零
```

### 第 4 页｜值不值得试

目标：给出明确但克制的推荐判断。

```text
栏目名：零号拆解
页码：4/4

主标题：
<项目名> 值不值得试？

推荐指数：
★★★★☆
4.5 / 5 或 4.7 / 5

雷达评分：
- 易用性
- 实用价值
- 扩展性
- 工程完整度
- 可持续性 / 社区活跃度

适合人群：
1. <人群 1>
2. <人群 2>
3. <人群 3>
4. <人群 4>

优势亮点：
1. <优势 1>
2. <优势 2>
3. <优势 3>
4. <优势 4>

一句提醒：
<说明真实门槛、限制、风险或合规提醒>

本期总判断：
如果你想 <目标>，<项目名> 是非常值得收藏和尝试的一套基础设施。

署名：
@NullByte·零
```

---

## 5. 视觉风格规则

### 必须使用

- 中文科技编辑风
- 暖白色背景
- 羊皮纸灰纹理
- 深棕色信息卡
- 琥珀橙 / 焦糖橙 / 铜橙强调色
- 圆角卡片
- 细分割线
- 强留白
- 清晰中文标题
- 简洁线性图标
- 信息层级清楚
- 底部深色金句条
- 固定署名：`@NullByte·零`

### 禁止使用

- 蓝紫霓虹
- 赛博朋克
- 高饱和渐变
- 过度 3D
- 一张图里放四页
- 四宫格拼图
- 漫画风
- 花哨 UI
- 无法阅读的小字
- 伪造官方 Logo
- 过度标题党

---

## 6. 图片生成统一提示词模板

每一页生成时都要使用以下基础模板，并替换具体内容。

```text
Create one standalone Chinese tech editorial poster for @NullByte·零.
IMPORTANT: single poster only, vertical 4:5, not a collage, not a grid, not four panels.
Style: warm off-white parchment background, dark brown information cards, amber orange accents, clean Chinese typography, rounded cards, thin dividers, generous whitespace.
Tone: calm, premium, high-trust, modern open-source editorial.
Layout: one page, one focus, mobile-readable, clear hierarchy.
Add top-left label: 零号拆解.
Add top-right page number: <1/4 or 2/4 or 3/4 or 4/4>.
Add bottom signature: @NullByte·零.
Avoid: blue-purple neon, cyberpunk, clutter, unreadable tiny text, fake logos, copied UI, 2x2 grid, split-screen collage.
```

---

## 7. 四页图片具体提示词模板

### 图片 1 Prompt

```text
Create one standalone vertical 4:5 Chinese editorial poster.
Page number: 1/4.
Project: <项目名>.
Title: 今日分享开源项目 <项目名>.
Subtitle: <一句话定位>.
Show a concept architecture diagram on the right: user/agent -> <项目核心> -> outputs/content.
Show project signal cards: GitHub Stars, Forks, Commits/Release, License.
Show core capabilities as numbered list.
Bottom quote: <第1页金句>.
Warm off-white parchment background, dark brown cards, amber orange accents.
Not a collage, not a grid, not four panels.
Signature: @NullByte·零.
```

### 图片 2 Prompt

```text
Create one standalone vertical 4:5 Chinese editorial poster.
Page number: 2/4.
Title: 为什么推荐 <项目名>？
Subtitle: <推荐理由一句话>.
Left side: 4 recommendation cards with icons and short explanations.
Right side: supported platforms / capability matrix / typical workflow.
Bottom quote: <第2页金句>.
Warm off-white parchment background, dark brown cards, amber orange accents.
Not a collage, not a grid, not four panels.
Signature: @NullByte·零.
```

### 图片 3 Prompt

```text
Create one standalone vertical 4:5 Chinese editorial poster.
Page number: 3/4.
Title: <项目名> 解决了什么问题？
Subtitle: <从旧状态到新状态>.
Top flow: user -> task/question -> <项目名> -> platform/tool/content -> answer/summary.
Middle layout: left column common pain points, right column project solutions.
Bottom quote: <第3页金句>.
Warm off-white parchment background, dark brown cards, amber orange accents.
Not a collage, not a grid, not four panels.
Signature: @NullByte·零.
```

### 图片 4 Prompt

```text
Create one standalone vertical 4:5 Chinese editorial poster.
Page number: 4/4.
Title: <项目名> 值不值得试？
Show rating: <评分>/5 with stars.
Show radar chart with 5 dimensions.
Show suitable audience list.
Show advantages list.
Show one caution note.
Bottom final judgment quote: <第4页总判断>.
Warm off-white parchment background, dark brown cards, amber orange accents.
Not a collage, not a grid, not four panels.
Signature: @NullByte·零.
```

---

## 8. 标题规则

必须输出：

- 1 个主标题
- 4-6 个备选标题

标题要求：

- 有痛点
- 有项目信号
- 有明确价值
- 不夸张
- 不编造数据
- 适合公众号 / 微头条 / 抖音图文

标题模板：

```text
<Stars> Star！这个项目把 <项目能力> 做成了可复用基础设施
```

```text
别再让 Agent 看不见互联网了，<项目名> 给出了一套工程化方案
```

```text
<项目名>：让 AI Agent 从“会回答”升级到“会读取、会搜索、会执行”
```

```text
零号拆解｜<项目名>：一个值得收藏的 <项目方向> 开源项目
```

---

## 9. 文案规则

### 公众号配图文案

字数：100-180 字。  
必须包含：项目名、项目方向、推荐理由、解决的问题、适合人群。

模板：

```text
今天分享一个值得关注的 AI 开源项目：<项目名>。

它不是 <容易误解的定位>，而是一个 <准确定位>。真正有价值的地方，是它把 <核心能力> 做成了一套可安装、可复用、可持续维护的工程能力。

如果你正在做 <目标场景>，或者希望让 Agent 具备 <关键能力>，这个项目值得收藏。
```

### 微头条短文案

字数：60-120 字。

```text
今天挖到一个很适合 Agent 开发者收藏的项目：<项目名>。

它把 <核心能力1>、<核心能力2> 和 <核心能力3> 做成一套工具层，让 Agent 不只是会回答，而是真的能 <核心动作>。
```

### 话题标签

每次输出 3-6 个。

```text
#AI开源项目# #GitHub# #AIAgent# #MCP# #开源项目推荐# #开发者工具#
```

---

## 10. 最终交付格式

```markdown
## 本期项目
<项目名>

## 主标题
<主标题>

## 备选标题
1. <标题1>
2. <标题2>
3. <标题3>
4. <标题4>
5. <标题5>

## 公众号配图文案
<文案>

## 微头条短文案
<文案>

## 话题标签
#标签1# #标签2# #标签3# #标签4#

## 事实核验
<仓库地址 / Stars / Forks / Commits / License / Release / 最近更新 / README 核心能力>

## 配图
已生成 4 张独立竖版图：
1. <图片1>
2. <图片2>
3. <图片3>
4. <图片4>
```

---

## 11. 示例调用

```text
依据这个 skills，直接完整输出一期今日分享项目：
https://github.com/Panniantong/Agent-Reach
包含标题、文案、标签和 4 张图。
```

```text
依据这个 skills，直接完整输出一期今日分享项目，选一个最近有更新、适合 Agent 开发者收藏的项目。
```

```text
依据这个 skills，先给我看一期草稿，暂时不要出图。
```

---

## 12. 质量检查清单

交付前检查：

- [ ] 是否联网核验了项目？
- [ ] 是否没有编造数据？
- [ ] 是否输出了主标题？
- [ ] 是否输出了备选标题？
- [ ] 是否输出了公众号文案？
- [ ] 是否输出了微头条文案？
- [ ] 是否输出了话题标签？
- [ ] 是否输出了事实核验？
- [ ] 是否生成了 4 张图？
- [ ] 是否 4 张图都是独立竖版？
- [ ] 是否没有生成四宫格？
- [ ] 是否统一暖白 + 橙色 + 深棕风格？
- [ ] 是否每张图都有页码和 @NullByte·零？
