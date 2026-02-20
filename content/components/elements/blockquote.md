---
title: Blockquotes
slug: "blockquotes"
date: 2025-10-29
tags: ["elements"]
coverLight: "images/elements/covers/blockquote_light.png"
coverDark: "images/elements/covers/blockquote_dark.png"
---

A blockquote element rendered from standard Markdown `>` syntax. Supports plain quotations and styled alert (admonition) blockquotes with configurable colors, icons and header text.

<!--more-->

## Features
- Supports blockquotes using standard Markdown syntax (`>`).
- Supports alert/admonition blockquotes using syntax like `> [!NOTE]` with default styles for different types (info, note, tip, warning, important, caution).
- Supports custom colors, icons and header text for alert blockquotes via attributes.

## Syntax
Basic blockquote:

```markdown
> This is a simple blockquote.
```

Alert / admonition blockquote:

```markdown
> [!STYLE]
> Helpful advice or tip goes here.
```

Provide attribute overrides using curly-brace attributes after blockquote definition:

```markdown
> [!STYLE] Optional Title
> Blockquote content.
{color="#e91e63" icon="heart" textcolor="#fff"}
```

## Components & attributes
style
: Alert type (e.g. `INFO`, `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION`).

color
: Accent color used for header / left border (accepts any valid CSS color).

textColor
: Color for header text, use along with `color` to provide a readable contrast.

icon
: Override the default icon, using theme's icon set (e.g. FontAwesome names like `circle-info` or `lightbulb`).
: Pass an empty value (e.g. `icon=""`) to hide the icon for an alert.

iconStyle
: Icon style (e.g. `solid`, `regular`, `brands`), defaults to `solid`.

### Default alert styles
| Type     | Title | Icon           | Color |
|---------|-------------|:-----------------------:|-------------|
| INFO     | Info          | {{< icon name="circle-info" >}}          | {{< mark style="info" >}}`#0057b8`{{< /mark >}}     |
| NOTE     | Note          | {{< icon name="pen-to-square" >}}        | {{< mark style="note" >}}`#ffc107`{{< /mark >}}     |
| TIP      | Tip           | {{< icon name="lightbulb" >}}            | {{< mark style="tip" >}}`#00bcd4`{{< /mark >}}     |
| WARNING  | Warning       | {{< icon name="circle-exclamation" >}}   | {{< mark style="warning" >}}`#ff9900`{{< /mark >}}     |
| IMPORTANT| Important     | {{< icon name="star" >}}                 | {{< mark style="important" >}}`#6200ea`{{< /mark >}}     |
| CAUTION  | Caution       | {{< icon name="triangle-exclamation" >}} | {{< mark style="caution" >}}`#ff5500`{{< /mark >}}     |

## Examples

### Example 1: Simple blockquote

```markdown
> "There is no place like home." — Example
```

**Output:**
> "There is no place like home." — Example

### Example 2: Alert blockquote

```markdown
> [!INFO]
> This is an informational message.

> [!NOTE]
> Remember to save your work frequently.

> [!TIP]
> Use `--dry-run` first to avoid surprises.

> [!WARNING]
> This action cannot be undone.

> [!IMPORTANT]
> Ensure you have a backup before proceeding.

> [!CAUTION]
> High voltage area — proceed with care.
```

**Output:**
> [!INFO]
> This is an informational message.

> [!NOTE]
> Remember to save your work frequently.

> [!TIP]
> Use `--dry-run` first to avoid surprises.

> [!WARNING]
> This action cannot be undone.

> [!IMPORTANT]
> Ensure you have a backup before proceeding.

> [!CAUTION]
> High voltage area — proceed with care.


### Example 3: Alert with custom title, color and icon

```markdown
> [!NOTE] A Love Letter
> Blockquote content.
{color="#e91e63" icon="heart" textcolor="#fff"}
```

**Output:**
> [!NOTE] A Love Letter
> Blockquote content.
{color="#e91e63" icon="heart" textcolor="#fff"}

### Example 4: Alert without icon

```markdown
> [!WARNING]
> This action is irreversible.
{icon=""}
```

**Output:**
> [!WARNING]
> This action is irreversible.
{icon=""}

### Example 5: Wide blockquote
Wrap any blockquote in the `wide` partials to span width of viewport.

```markdown
{{</* wide */>}}
> [!IMPORTANT]
> Database migration required — schedule downtime.
{{</* /wide */>}}
```

**Output:**
{{< wide >}}
> [!IMPORTANT]
> Database migration required — schedule downtime.
{{< /wide >}}
