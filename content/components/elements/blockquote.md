---
title: Blockquotes
slug: "blockquotes"
date: 2025-10-29
tags: ["elements"]
coverLight: "images/elements/covers/blockquote_light.png"
coverDark: "images/elements/covers/blockquote_dark.png"
---

A blockquote element rendered from standard Markdown syntax. Supports plain quotations and styled alert (admonition) blockquotes with configurable colors, icons and header text.

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

Provide attribute using curly-brace attributes under blockquote definition:

```markdown
> [!STYLE] Optional Title
> Blockquote content.
{color="#e91e63" icon="heart" textcolor="#fff"}
```

### Parameters
Style
: (required) Alert type (e.g. `INFO`, `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION`, `ACCENT`, `NONE`).

Title
: (optional) Custom title for the alert header (defaults to capitalized style name).

Additional Attributes
: Additional attributes can be added in curly braces after blockquote content.
  
  color
  : Accent color used for header / left border (accepts   any valid CSS color).
  
  textcolor
  : Color for header text, use along with `color` to   provide a readable contrast.
  
  icon
  : Override the default icon, using theme's icon set (e.  g. FontAwesome names like `circle-info` or `lightbulb`).
  
  iconstyle
  : Icon style (e.g. `solid`, `regular`, `brands`),   defaults to `solid`.

### Default alert styles
| Style     | Title | Icon           | Color |
|---------|-------------|:-----------------------:|-------------|
| INFO     | Info          | {{< icon name="circle-info" >}}          | {{< mark style="info" >}}`#0057b8`{{< /mark >}}     |
| NOTE     | Note          | {{< icon name="pen-to-square" >}}        | {{< mark style="note" >}}`#ffc107`{{< /mark >}}     |
| TIP      | Tip           | {{< icon name="lightbulb" >}}            | {{< mark style="tip" >}}`#00bcd4`{{< /mark >}}     |
| WARNING  | Warning       | {{< icon name="circle-exclamation" >}}   | {{< mark style="warning" >}}`#ff9900`{{< /mark >}}     |
| IMPORTANT| Important     | {{< icon name="star" >}}                 | {{< mark style="important" >}}`#6200ea`{{< /mark >}}     |
| CAUTION  | Caution       | {{< icon name="triangle-exclamation" >}} | {{< mark style="caution" >}}`#ff5500`{{< /mark >}}     |
| ACCENT   | Alert         | —                                         | {{< mark style="accent" >}}`--color-accent`{{< /mark >}}     |
| NONE     | Alert         | —                                         | {{< mark style="none" >}}`--color-bg`{{< /mark >}}     |
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

> [!ACCENT]
> This is an accent alert with theme's accent color.

> [!NONE]
> This is a neutral alert without special styling.
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

> [!ACCENT]
> This is an accent alert with theme's accent color.

> [!NONE]
> This is a neutral alert without special styling.

### Example 3: Alert with custom title, color and icon

```markdown
> [!NONE] Python 3.11 Required
> Make sure to upgrade your Python version to 3.11.
{color="#77a03d" textcolor="#ffffff" icon="python" iconstyle="brands"}
```

**Output:**
> [!NONE] Python 3.11 Required
> Make sure to upgrade your Python version to 3.11.
{color="#77a03d" textcolor="#ffffff" icon="python" iconstyle="brands"}

### Example 4: Wide blockquote
Wrap any blockquote in the `wide` shortcode to span width of viewport.

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
