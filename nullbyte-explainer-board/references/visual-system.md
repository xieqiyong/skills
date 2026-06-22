# NullByte Explainer Board Visual System

Use this reference when the user wants prompts, layouts, or actual images.

## Core Direction

Recreate the `reading experience` of a friendly technical whiteboard:

- one image explains one concept
- colorful but not noisy
- hand-drawn but still structured
- cute but still technically clear

This skill intentionally differs from the darker `NullByte` editorial styles. Default to a bright, playful, notebook-like explainer look.

## Default Palette

Prefer a soft multi-color pastel system:

- `墨蓝`: main title, key labels, body emphasis
- `天空蓝`: info cards, flow arrows, left-side inputs
- `薄荷绿`: success states, merged results, positive comparisons
- `奶油黄`: warnings, intermediate highlights, helper tags
- `薰衣草紫`: central mechanism blocks, neutral compare areas
- `桃粉`: numbered chips, note labels, gentle warnings
- `橙杏色`: bottom summary strip or supporting emphasis
- `白底 + 淡灰阴影`: keep the whole board airy

Avoid:

- dark backgrounds
- fluorescent neon
- heavy gradients
- monochrome corporate decks

## Typography Direction

- Main Chinese title: friendly handwritten or marker-like feel, oversized, dark ink color
- Subtitle: lighter, still readable, can mix one English product word
- Section labels: rounded sticker / brush tab style
- Body copy: simple, compact, high legibility
- Code or JSON snippets: neat monospace inside soft cards

## Layout Language

Preferred visual ingredients:

- rounded cards
- thin colored outlines
- dashed compare boxes
- hand-drawn arrows
- tiny sparkles, stars, underline marks, stickers
- numbered section chips like `1.` `2.` `3.`
- a bottom conclusion ribbon or note bar

The page should feel like a teacher or engineer sketched the concept for teammates, then polished it just enough for publishing.

## Page Anatomy

Default single-board structure:

1. Big title row
2. One subtitle or one-line explanation
3. `3` main explanation zones
4. Centerpiece mechanism or comparison block
5. Bottom summary strip

If the user asks for a denser version:

- use `4-5` zones max
- never exceed `2` visual levels of nesting
- keep at least one large empty margin area so the board can breathe

## Diagram Elements

Use these elements when they improve understanding:

- cute robot / agent icons
- boxes labeled `State`, `Input`, `Output`, `Result`
- mini JSON or pseudo-code snippets
- merge / split arrows
- checkmark vs cross comparison
- before / after labels
- smile / sad reaction icons for contrast

Do not add decorative mascots that do not explain anything.

## Brand Rules

- Put `@NullByte·零` subtly at the bottom-right by default.
- If the bottom strip is too crowded, move the signature to the top-right in small type.
- Keep the brand smaller than section labels and much smaller than the title.

## Prompt Template

```text
Create a friendly Chinese technical explainer board, landscape 3:2, bright whiteboard style, cute but clear, premium self-media educational graphic for @NullByte·零.

Visual style: white background, dark ink title, pastel multi-color section cards, hand-drawn arrows, rounded boxes, dashed comparison areas, tiny sparkles and underline marks, structured like a polished notebook explanation.

Text hierarchy:
- Main title: "<主标题>"
- Subtitle: "<副标题>"
- Section 1 label and content: "<内容>"
- Section 2 label and content: "<内容>"
- Section 3 label and content: "<内容>"
- Bottom takeaway: "<总结>"

Include: <center mechanism / inputs / outputs / comparison blocks / mini JSON or code snippets>.
Tone: approachable, visual, easy to understand at a glance, bookmark-worthy.

Avoid: dark cyberpunk, corporate slide deck, dense paragraphs, copied screenshot layout, tiny unreadable text.
```

## Output Guidance

- If the user asks for prompts only, return:
  - one main prompt
  - one alternate prompt with a slightly cleaner / less cute layout
- If the user asks for a single image, default to one landscape explainer board
- If the user asks for a bundle, generate:
  - main principle board
  - detailed compare or breakdown board
  - takeaway board
