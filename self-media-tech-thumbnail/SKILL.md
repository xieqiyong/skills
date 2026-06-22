---
name: self-media-tech-thumbnail
description: 生成强视觉冲击力的中文自媒体 AI 与科技类封面图提示词和成品图，采用头条式戏剧化视觉语言。当用户为 AI 工具、编程、模型发布、产品对比、创始人动态或趋势评论制作视频封面、缩略图、标题图或封面图时使用，尤其是用户只给了标题、脚本、要点或粗糙文案，却想要与内置参考图同款高对比风格时。
---

# Self Media Tech Thumbnail

Turn a topic or block of copy into a ready-to-generate thumbnail prompt, then generate the image when the user asks for a cover. Default output is a `16:9` landscape thumbnail optimized for Chinese self-media feeds.

## Workflow

1. Open `references/style-system.md` when the request says "类似这种风格", "照这个做", or needs a closer match to the bundled example.
2. Default to `16:9` unless the user names another format.
3. Compress the user's copy into a three-level text hierarchy:
   - `kicker`: 4-10 Chinese characters, usually authority, urgency, or surprise
   - `main headline`: 8-18 Chinese characters, optionally keep one English product name for recognition
   - `support line`: 8-18 Chinese characters, usually contrast, result, conflict, or payoff
4. Choose the focal visual:
   - Use a person when the topic centers on a founder, engineer, or public figure.
   - Use product UI, code, or interface cards when the story centers on a tool or feature.
   - Use a versus layout only when the story is explicitly comparative.
5. Build the image prompt with the style rules below.
6. If the user asks for a cover image, thumbnail, or封面图, call `image_gen` directly. If the user asks only for文案 or提示词, return the text pack and the generation prompt.

## Style Rules

- Make the composition bold and asymmetrical. Default to a heavy title block on the left and the main subject on the right.
- Use a dark graphite, navy, or black background with electric blue plus warm orange or red accent lighting.
- Make the main Chinese headline oversized, condensed, and extremely readable on mobile.
- Favor white for the core Chinese claim, yellow for the key English product word, and cyan or blue for secondary UI text.
- Add `2-4` supporting modules such as a checklist card, code panel, feature strip, product UI card, or comparison badge.
- Use depth, drop shadow, glow, rim light, and diagonal motion cues to create a premium breaking-news feel.
- Keep the image dense but controlled. Every supporting element must reinforce the headline.
- Prefer photorealistic人物, crisp UI, sharp typography, and clean edge lighting.

## Avoid

- Do not recreate the bundled reference image verbatim.
- Do not rely on soft pastel palettes, tiny text, or flat minimal layouts.
- Do not let visual effects bury the main headline.
- Do not exceed four text blocks.
- Do not use exact logos or celebrity likenesses unless the user explicitly asks for them.

## Prompt Template

Use a prompt in this shape and fill in the content:

```text
Create a bold Chinese self-media AI/tech video thumbnail, 16:9, optimized for mobile feed readability. Dark high-contrast cinematic background with electric blue and warm orange/red lighting, premium editorial tech aesthetic, oversized condensed Chinese headline text with strong depth and shadow. Main focal subject: <subject>. Left-heavy text composition, right-side hero visual, supporting UI panels and code/product elements, subtle lightning or motion streaks, dramatic contrast, sharp edges, glossy highlights.

Headline text:
Top kicker: "<kicker>"
Main headline: "<main headline>"
Support line: "<support line>"
Optional corner line: "<optional short CTA or trend line>"

Visual cues: <2-4 supporting elements>.
Mood: breaking-news, high authority, high click-through, polished, not cluttered.
No watermark, no unrelated text, no blurry typography.
```

## Copy Compression

When the user gives long copy, reduce it to:

- the claim
- the object
- the tension

Examples:

- claim: `官方下场`
- object: `Claude 提示词`
- tension: `为什么很多人还是写不好`

If the user provides only a topic, invent concise cover copy that sounds native to Chinese self-media, then build the prompt from that.

## Output Modes

- If the user asks for `封面`, `缩略图`, `出图`, or `来张图`, generate the image directly.
- If the user asks for `标题`, `封面文案`, or `提示词`, return:
  - one primary headline pack
  - one ready-to-use image prompt
- If the user asks for several options, vary the hook and support line while keeping the same visual system.

## Bundled Resources

- Style notes: `references/style-system.md`
- Visual anchor: `assets/reference-grok-build.png`

Open the bundled style notes when you need a refresher on composition, color, or module choices. Use the reference image only as a style anchor, not as a frame to copy element-for-element.
