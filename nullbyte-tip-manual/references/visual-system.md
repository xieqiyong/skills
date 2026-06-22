# NullByte Tip Manual Visual System

Use this reference when the user wants prompts, layouts, or actual images.

## Core Direction

Recreate the `reading experience`, not the exact pixels.

Preserve:

- clear manual feel
- dense but readable information
- strong title + table + note box structure
- bookmark-worthy usefulness

Allow stronger similarity in:

- page hierarchy
- table-first manual feel
- title placement
- note-box rhythm

Change:

- color system
- typography rhythm
- block shapes
- brand expression

## Brand Rules

- Put `@NullByte·零` at the top-right corner by default.
- Keep the brand clear but smaller than the main title.
- If page numbers are used, let them sit below or left of the brand, not replace it.

## Default Palette

Main palette for this skill:

- `暖陶橙`: warm terracotta orange for titles and structure
- `砖橙`: muted brick orange for highlights, tags, table headers, emphasis
- `米白`: warm off-white for the page background
- `雾灰`: soft gray for lines, cards, and neutral modules

Optional secondary accent:

- `浅杏橙`: for soft fills and bottom note boxes

Suggested tone:

- calm
- premium
- practical
- editor-designed

Avoid:

- fluorescent orange
- purple bias
- neon cyberpunk
- over-glossy startup deck style

## Typography Direction

- Chinese headline: bold, compact, highly readable
- English kicker: small, spaced, editorial
- Body text: clean, simple, table-friendly
- Numeric page markers: light, quiet, secondary

## Page Types

### Cover Page

Best for:

- a big theme
- command manual title
- "这一期讲什么"

Recommended structure:

- thin accent line at the very top
- small bilingual kicker at top-left
- `@NullByte·零` at top-right
- big Chinese title in the middle
- one subtitle line explaining the scope
- one short sentence describing why it matters

### Table Page

Best for:

- command lists
- tool option summaries
- feature explanations

Recommended structure:

- thin accent line at the very top
- title block
- two-column table
- left column: command / concept / action
- right column: short explanation
- one bottom note box with combo advice or path suggestion

### Summary Page

Best for:

- usage combos
- beginner path
- mistake reminders
- setup suggestions

Recommended structure:

- thin accent line at the very top
- title
- `3-5` grouped tips
- one highlighted path box
- optional footer line

## Reference-Like Manual Structure

Use this when the user gives a screenshot similar to a "command manual" page and asks to imitate the feel.

Preferred hierarchy:

- very top thin color bar
- upper-left bilingual mini label
- upper-right `@NullByte·零`
- optional nearby page marker like `01 / 03`
- centered main title
- one centered subtitle sentence
- rounded two-column table
- rounded bottom note box

This structure can be highly similar in reading flow, but must still change:

- colors
- exact text
- spacing rhythm
- border rounding
- table proportions

## Prompt Template

```text
Create a polished Chinese Toutiao knowledge-card graphic for @NullByte·零.
Format: portrait 4:5, premium editorial practical-tech style.
Do not copy the source image layout; keep only the clear manual reading experience.

Brand: place "@NullByte·零" at the top-right corner.
Color system: warm terracotta orange, muted brick orange, warm off-white, soft gray.
Tone: calm, premium, practical, bookmark-worthy.
Layout type: <cover page / table page / summary page>.

Text to render:
- Kicker: "<small top-left English + Chinese label>"
- Main title: "<main Chinese title>"
- Subtitle: "<subtitle>"
- Content blocks: "<table rows or grouped tips>"
- Bottom note: "<one highlighted note>"
- Optional page number: "<01 / 03>"

Use rounded cards, thin dividers, clear tables, restrained shadows, strong Chinese readability, and a fresh original layout with a manual-page feel.
Avoid copied phrasing, clutter, unreadable tiny text, fluorescent orange, and generic AI poster style.
```

## Output Guidance

- If the user asks for prompts only:
  - return one main prompt
  - return one alternate prompt with a darker palette
- If the user asks for a visual bundle:
  - generate cover + content page + summary page
- If the user gives long text:
  - compress first
  - then design
