# NullByte Content System

Use this reference when the request needs a stable栏目结构, a roundup, a single-project breakdown, or multiple copy variants.

## Editorial Spine

- Treat the package as a `signal filter`, not a `热度搬运`.
- Make every item answer three things:
  - `它是什么`
  - `为什么值得注意`
  - `谁应该花时间看`
- Keep the order of importance: judgment first, clarity second, style third.

## Board Page Recipe

Use this when the user wants a leaderboard-like page, a roundup card, or a weekly精选页.

```markdown
栏目名
一句话判断 / 本期筛选标准

1. 项目或事件名
一句话结论
标签：立刻试 / 值得跟 / 先收藏 / 观察中

2. ...
```

Rules:

- Keep the page to `4-8` or `4-10` items max.
- Keep each item to `2-3` short lines.
- Add metrics only when the user provides real numbers or links.
- If there is only one item, switch to the single project breakdown recipe instead of forcing a board.
- End with `本期总判断`, `下一步观察`, or `下期值得继续跟`, not a generic CTA.

## Featured Detail Page Recipe

Use this when the user wants the second screen, a single-item card, or a deeper explain-like-I'm-busy breakdown.

```markdown
标题
一句话结论

它是什么
为什么这次值得看
真正亮点 / 真正门槛
适合谁
怎么开始
一句提醒
```

Rules:

- Put the verdict before the background.
- Keep company history short unless it directly explains the value.
- Finish with a practical next step whenever possible.

## Single Project Breakdown Recipe

Use this when the user gives one project, one repo, one product launch, or directly asks for `项目拆解`.

```markdown
标题
一句话判断

它解决什么问题
为什么现在值得看
真正亮点
真实门槛 / 注意点
适合谁
要不要现在试
```

Rules:

- Do not force rank words such as `第1` or `TOP`.
- Use direct recommendation language: `值不值得试`, `适不适合你`, `现在该不该跟`.
- Add a short comparison line only when it helps the reader judge faster.

## Single Project 3-Image Copy Recipe

Use this when the user gives one project and says `出图`, `做图`, `直接生成`, or otherwise clearly wants images first.

### Image 1: Cover

```markdown
栏目名
主标题
副标题
一句话判断
推荐理由
```

Rules:

- Keep it hook-first.
- The `推荐理由` should be a clear benefit, not a generic compliment.
- Do not place installation commands or long URLs here by default.

### Image 2: Install / Address / Usage

```markdown
开源地址
安装方式
使用技巧 / 上手提示
```

Rules:

- Put the repo address here.
- Keep commands short and mobile-readable.
- If the material has both install steps and usage tips, prefer one short tip instead of crowding too many commands.

### Image 3: Insight / Reflection

```markdown
心得和思考
为什么值得看
适合谁 / 什么时候用
一句提醒
```

Rules:

- This page should feel like judgment, not documentation.
- End on one calm takeaway instead of hype.
- If the source material is thin, keep this card sparse rather than padding it.

## Category Lenses

### AI资讯

Ask:

- 这是单点新闻，还是趋势信号？
- 它会改变谁的工作流、预算、注意力？

Good item pattern:

- `发生了什么`
- `为什么值得看`
- `接下来观察什么`

### 开源项目

Ask:

- 它解决的是真痛点，还是包装概念？
- 与现有方案相比，快在哪里、省在哪里、稳在哪里？

Good item pattern:

- `解决什么问题`
- `真正亮点`
- `上手门槛`
- `适合谁`

### 技巧

Ask:

- 这是一次性噱头，还是可复用的方法？
- 它省的是时间、成本，还是认知负担？

Good item pattern:

- `适用场景`
- `关键动作`
- `收益`
- `注意事项`

## NullByte Label System

Prefer these labels over generic heat markers:

- `立刻试`: practical and ready now
- `值得跟`: not fully mature but the trend is real
- `先收藏`: useful later, not urgent now
- `观察中`: interesting, but signal still weak
- `别上头`: attention is high, certainty is low

Use at most one label per item.

## Naming Ideas

Pick one naming system per post instead of mixing all of them:

- `零号信号榜`
- `本周值得看`
- `零号拆解`
- `工具观察`
- `开源雷达`
- `今天别错过`
- `能不能马上用`

## Anti-Copy Checklist

Before finalizing, verify:

- Section names are original
- The ordering is not identical to the reference screenshots
- No fake metrics or false precision appear
- The copy sounds like `@NullByte·零`, not a generic tech news account
- The strongest judgment is visible in the first screen

## Fast Output Combinations

- `只有链接`: make a board page with short verdicts
- `只有一个项目`: make a standalone breakdown page with no ranking language and optionally add a short comparison line
- `只有一个项目且用户说出图`: make a `3`-image set: cover, install/address/tips, and insight/reflection
- `混合素材`: make one main board plus a `顺手一提` block
- `用户说“仿照这个”`: borrow scanability and list/detail rhythm, not labels, phrasing, or information architecture
