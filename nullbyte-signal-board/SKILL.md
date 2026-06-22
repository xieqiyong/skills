---
name: nullbyte-signal-board
description: 为 AI 资讯、开源项目、开发者工具和工作流技巧，策展中文自媒体信号榜、单项目拆解以及配套视觉概念。当用户想要榜单式汇总、排名清单、“本周值得看”、“AI 资讯精选”、“开源项目推荐”、“技巧整理”、“项目拆解”、单项目深度解读、三图项目卡套图、榜单页+详情页，或基于链接、截图、笔记、要点生成配套封面/卡片/海报图时使用。把原始素材转成 @NullByte·零 风格的原创、非搬运文案，带明确判断、可扫读结构、受众指引，以及可选的图解提示词或直接出图；截图仅作灵感，绝不照搬原文。
---

# Nullbyte Signal Board

Turn links, screenshots, notes, or rough picks into an editorial package that feels like `@NullByte·零` did the filtering for the reader. Default priority: help the audience answer three questions fast: `what matters`, `why now`, and `who should care`. When the user asks for visuals, extend the same judgment into a cover, board card, or multi-card single-project set based on whether the material is a roundup or a single item instead of treating images as a separate style exercise.

## Workflow

1. Identify the dominant content lane:
   - `AI资讯`: launches, updates, funding, policy, ecosystem shifts
   - `开源项目`: repositories, frameworks, agents, infra, tools
   - `技巧`: prompts, workflows, automation setups, practical methods
2. Choose the output mode:
   - `榜单页`: `6-10` items, fast scan, one sharp judgment per item
   - `单项目拆解页`: one project or event, deeper explanation and practical guidance, no ranking required
   - `成套内容`: 榜单页 first when there are multiple items, then `1-3` detail pages for the strongest items
   - `视觉套件`: cover image, board poster, single-project three-card set, or a mixed copy-plus-visual pack
3. Judge by signal, not by empty hype.
   - If there are multiple items, rank by:
     - `信号强度`: does it change behavior, workflow, or market attention?
     - `可落地性`: can readers try or benefit from it soon?
     - `信息密度`: is there real substance behind the headline?
     - `提前量`: does noticing it early create an edge?
   - If there is only one item, skip ranking and use the same dimensions to decide the verdict, the angle, and whether it is worth immediate action.
4. Decide the board angle or breakdown angle before writing. Good angles:
   - `本周最值得跟进`
   - `马上能试`
   - `值得收藏`
   - `先观察别上头`
   - `这次到底值不值得试`
   - `真正亮点和真实门槛`
5. Write with the `@NullByte·零` voice:
   - lead with judgment, then explain
   - translate technical value into plain Chinese
   - stay sharp and calm; do not overhype
6. If the user asks for `配图`, `封面`, `卡片`, `海报`, `来一张图`, or `顺手做视觉`, open `references/visual-system.md`.
7. Open `references/content-system.md` when the user wants a closer structural match to a list/detail page, needs multiple variants, or asks for a repeatable栏目 format.

## Defaults

If the user says "按这个做一期" without specifying format and the material contains multiple items, return:

- one board title
- one short intro line with the filter angle
- `6-8` ranked items
- one featured detail page for the top item
- a closing署名 line: `@NullByte·零`

If the user gives only one project or event without specifying format, return:

- one title
- one short verdict line
- one single-project breakdown page
- one practical next-step block or short comparison line when useful
- a closing署名 line: `@NullByte·零`

If the user says "连图一起做" without specifying image format:

- for multi-item material, return:
  - one board page copy
  - one featured detail page
  - one cover prompt
  - one board card prompt
  - one featured detail card prompt
- for single-item material, return:
  - one single-project breakdown page
  - one cover prompt
  - one install-or-usage card prompt
  - one insight card prompt

If the user gives a single project and says only `做图`, `出图`, `直接生成`, or `只要出图`, treat it as `只要出图` and generate a `3`-image set by default:

- image `1`: 封面图
  - keep the current strong hook style
  - add one clear `推荐理由`
  - do not put installation commands or the repo address here unless the user explicitly asks
- image `2`: 安装 / 开源地址 / 使用技巧卡
  - include the GitHub or project address
  - include installation steps
  - include one short usage tip when the material supports it
- image `3`: 心得和思考卡
  - summarize why it matters
  - explain who should care or when to use it
  - end with one calm takeaway rather than hype

When the user says `只要出图`, do not first return a long article or prompt package unless they explicitly ask for copy.

Call `image_gen` directly when the user explicitly asks for actual images rather than prompts.

## Guardrails

- Do not copy section names, badge words, sentence rhythm, or layout logic from a reference page.
- Do not invent stars, growth numbers, downloads, or rank movements unless the user gives verified data.
- Do not force every roundup into a popularity chart. If the material is mixed, use `信号位`, `今日值得看`, or themed tiers instead of fake precision.
- Do not fabricate ranking language for a single project. Use verdicts, tags, comparisons, or a direct recommendation instead.
- For the default single-project `3`-image set, keep the repo address and installation info on image `2`, not image `1`, unless the user explicitly asks for a different order.
- Treat screenshots as structural inspiration only. Build a new naming layer and a new editorial order.
- Prefer one clear point of view over decorative filler.
- Do not make visuals look like a traced screenshot. Keep the scanability, but rebuild typography, labels, hierarchy, and framing.
- When generating images, prefer fewer stronger claims on the first screen rather than stuffing all `5-10` items into one cluttered canvas.

## Visual Workflow

1. Decide the visual type:
   - `封面图`: one strong hook, one hero item, built for click-through; for a single project, add one concise `推荐理由`
   - `榜单卡片`: use only when there are multiple items or the user explicitly wants a ranked-board look
   - `安装技巧卡`: for repo address, installation, and one practical usage tip
   - `心得思考卡`: for takeaways, audience fit, and one calm final judgment
   - `详情卡片`: use only when the user explicitly wants one standalone detail card instead of the default `3`-image set
2. Keep the text hierarchy tight:
   - `栏目名`: `4-8` Chinese characters
   - `主标题`: `8-18` Chinese characters
   - `副标题`: `10-22` Chinese characters
   - `角标`: optional, `2-6` Chinese characters
3. Use visual language that matches `@NullByte·零`:
   - clean editorial tech layout
   - warm off-white, ash charcoal, or deep brown-slate base
   - use orange as the default accent family, such as amber, tangerine, burnt orange, or copper
   - rounded cards, thin dividers, strong whitespace, and sharp information hierarchy
4. For actual images:
   - return prompts if the user asks for `提示词`, `文生图描述`, or `先给我方案`
   - call `image_gen` if the user asks for `做图`, `出图`, `来一张`, `直接生成`
   - for a single project, default to `3` separate images unless the user explicitly asks for only one image such as `来一张`
5. Reuse the same naming and label system from the copy. The visual should feel like the same栏目, not a second brand.

## Bundled Resources

- Formatting and copy system: `references/content-system.md`
- Visual system: `references/visual-system.md`

Open the references when you need category-specific page recipes, label systems, reusable section structures, or visual prompt scaffolding.
