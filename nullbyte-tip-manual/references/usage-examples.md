# Usage Examples

## Example 1

```text
Use $nullbyte-tip-manual 把这组 Claude Code 命令整理成 3 页头条知识卡，右上角固定 @NullByte·零，改成暖橙色手册风。
```

Expected behavior:

- choose `Preset A`
- compress long explanations
- output cover + command table + summary page

## Example 1B

```text
Use $nullbyte-tip-manual 参考这张命令手册图做一套橙色系版本，保留手册感和表格感，右上角固定 @NullByte·零。
```

Expected behavior:

- choose `Preset E`
- keep the manual-page reading rhythm
- switch to terracotta orange + brick orange palette
- avoid exact copying

## Example 1C

```text
Use $nullbyte-tip-manual 按 Claude Code 命令手册做 3 页橙色系版本，第一页写常用命令，第二页写项目命令，第三页写扩展命令，右上角固定 @NullByte·零。
```

Expected behavior:

- choose `Preset E`
- keep the thin top line, bilingual kicker, centered title, table block, and bottom note box
- use the successful 3-page command-manual rhythm from prior Claude Code examples

## Prompt Bundle Example

When the user asks for a close reference-like command manual, a good prompt shape is:

```text
Create page <01 / 03> of a Chinese Toutiao-style practical tech manual for @NullByte·零, portrait 4:5, premium editorial manual style, inspired by a command handbook reading experience but not copying any exact screenshot.

Use a warm orange palette: terracotta orange, muted brick orange, warm off-white, soft gray.
Put a very thin orange line across the very top.
Top-left small bilingual kicker: "<ENGLISH LABEL>" with smaller Chinese "<栏目副标>".
Top-right brand label: "@NullByte·零", with a subtle page marker nearby: "<01 / 03>".

Center large bold Chinese title: "<主标题>".
Below it a smaller centered subtitle in Chinese: "<副标题>".

Main body: a rounded two-column table with orange header row, left header "命令", right header "说明".
Include <6-8> rows exactly: "<row 1>" ... "<row N>".

Bottom: a rounded pale apricot-orange note box with title "<说明框标题>" and short Chinese body text explaining the recommended combo or setup path.

Add a tiny bottom-left footer label "<tool label>".
Strong readability, calm premium design, table-first structure, no clutter, not a pixel copy.
```

## Example 2

```text
Use $nullbyte-tip-manual 把这些 Cursor 使用技巧做成一套适合头条的实用技巧卡，先给我每页文案，再出图。
```

Expected behavior:

- return page-by-page copy first
- then generate visuals when asked

## Example 3

```text
Use $nullbyte-tip-manual 参考这张图的阅读感，把我的 ChatGPT 配置说明做成新的技巧手册，不要照抄原图配色和排版。
```

Expected behavior:

- keep manual feel
- rebuild layout and palette
- preserve `@NullByte·零` at top-right

## Example 4

```text
Use $nullbyte-tip-manual 把这篇长笔记压成 1 张收藏型知识卡。
```

Expected behavior:

- choose `Preset D`
- compress hard
- keep only the most useful `5-8` points
