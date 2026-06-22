# NullByte Visual System

Use this reference when the user wants the skill to produce prompts or images, not just copy.

## Core Principle

Do not recreate the reference screenshot. Recreate the `reading experience`:

- fast scan
- clear hierarchy
- strong first verdict or first item
- editorial trust

Everything else should be rebuilt in the `@NullByte·零` style.

## Recommended Visual Outputs

### Cover

Use when the post needs a main thumbnail or hero image.

Structure:

- top-left栏目标签
- large main title
- short subline
- one concise recommendation reason
- one featured repo or one themed cluster
- subtle radar or focus motif

Best for:

- `本周开源雷达`
- `5个值得跟的 AI 项目`
- `今天别错过`

### Board Card

Use when the user wants the actual ranked-board look or there are multiple items to show together.

Structure:

- board title
- subtitle or filter angle
- `3-6` visible rows
- each row keeps only: rank, name, one verdict, one small side metric or tag
- optional bottom fade or "展开 / 更多" cue

Rules:

- never cram all long descriptions into the image
- visually emphasize top `1-3`
- use whitespace to create trust

### Detail Card

Use when the user wants one project expanded into a single image. This is optional for single-project requests and should be used only when the user explicitly wants one standalone card instead of the default `3`-image bundle.

Structure:

- avatar or abstract repo badge
- repo name
- one-line verdict
- `3` metadata chips such as stars / category / barrier or "适合谁"
- one short paragraph block
- one "为什么值得看" block

### Install / Tips Card

Use for the second image in the default single-project image bundle.

Structure:

- repo name or project name
- open-source address
- `1-2` install lines
- `1` short usage tip or getting-started note

Rules:

- Prioritize readability over decoration.
- Commands and URLs should be large enough for mobile screens.
- Do not hide key commands inside faux code screenshots.

### Insight Card

Use for the third image in the default single-project image bundle.

Structure:

- short headline
- one takeaway
- `2-3` reflection blocks such as `为什么值得看`, `适合谁`, `一句提醒`

Rules:

- Keep this card editorial, not tutorial-heavy.
- Let whitespace carry the weight.
- The tone should feel thoughtful and grounded.

## Style Direction

- overall tone: calm, precise, premium tech editorial
- background: warm off-white, parchment gray, charcoal, or deep brown-slate
- accent: orange family only, prefer amber, apricot orange, burnt orange, or copper
- avoid purple bias
- avoid noisy neon sci-fi effects
- typography: heavy Chinese headline, clean body text, and numeric emphasis only when rankings are actually present

## Text Limits Inside Images

- cover: `2-3` text blocks max
- board card: title plus `3-6` item rows
- install / tips card: `3-5` content zones
- detail card: no more than `6` content zones
- insight card: `3-5` content zones

If the user gives too much text, compress it before prompting the model.

## Prompt Building Template

```text
Create a polished Chinese tech editorial social media graphic for @NullByte·零.
Format: <cover / board card / detail card / install-tips card / insight card>.
Visual tone: calm, premium, high-trust, modern open-source editorial.
Background: <warm off-white / charcoal / deep brown-slate>.
Accent color: <amber / apricot orange / burnt orange / copper>.
Layout: <specific structure>.
Typography: bold, highly readable Chinese headline, clean metadata chips, and numeric emphasis only when rankings are present.

Text to render:
- Column label: "<栏目名>"
- Main title: "<主标题>"
- Subtitle: "<副标题>"
- Optional rows or metadata: "<rows or chips>"

Support visuals: <repo avatar, abstract code graph, interface card, radar motif, focus frame, minimal glow>.
Avoid: copied layout, clutter, excessive neon, fake logos, unreadable small text.
```

## Default Single-Project Image Bundle

When the user gives one project and says only `出图`, `做图`, `直接生成`, or otherwise clearly wants images first, generate `3` separate images by default:

1. `封面图`
   - strong title
   - one-line verdict
   - one `推荐理由`
2. `安装 / 开源地址 / 使用技巧卡`
   - repo address
   - install method
   - one short usage tip
3. `心得思考卡`
   - why it matters
   - who should care
   - one calm takeaway

Do not collapse these three roles into one crowded canvas unless the user explicitly asks for a single-image summary.

## Output Rules

- If the user asks for prompts only, return:
  - for a single project default bundle: `3` prompts, one for each image
  - otherwise: one primary visual direction, one ready-to-use prompt, and one alternate prompt with a different angle
- If the user asks for actual images, call `image_gen` directly.
- If the request is a bundle, produce:
  - for multi-item material: `1` cover, `1` board card, and `1-3` detail cards
  - for single-item material: `1` cover, `1` install / tips card, and `1` insight card by default
