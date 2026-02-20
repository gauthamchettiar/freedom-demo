---
title: Blockquotes
slug: "blockquotes"
date: 2025-10-29
tags: ["elements"]
coverLight: "covers/elements/blockquote_light.png"
coverDark: "covers/elements/blockquote_dark.png"
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

Extras
: Below optional attributes can be added in curly braces after blockquote content, 
  
  color
  : Accent color used for header / left border (accepts   any valid CSS color).
  
  textcolor
  : Color for header text, use along with `color` to   provide a readable contrast.
  
  icon
  : Override the default icon, using theme's icon set (e.  g. FontAwesome names like   `circle-info` or `lightbulb`).
  
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

## Theming

All default styles provided above can be customized by overriding `layouts/_partials/utils/alert-styles.html`

```go {title="layouts/_partials/utils/alert-styles.html"}
{{- return dict
  "info" (dict "color" "#0057b8" "textColor" "#fff" "icon" "circle-info" "iconStyle" "solid" "title" "Info")
  "note" (dict "color" "#ffc107" "textColor" "#000" "icon" "pen-to-square" "iconStyle" "solid" "title" "Note")
  "tip" (dict "color" "#00bcd4" "textColor" "#000" "icon" "lightbulb" "iconStyle" "solid" "title" "Tip")
  "warning" (dict "color" "#ff9900" "textColor" "#000" "icon" "circle-exclamation" "iconStyle" "solid" "title" "Warning")
  "important" (dict "color" "#6200ea" "textColor" "#fff" "icon" "star" "iconStyle" "solid" "title" "Important")
  "caution" (dict "color" "#ff5500" "textColor" "#fff" "icon" "triangle-exclamation" "iconStyle" "solid" "title" "Caution")
  "accent" (dict "color" "var(--color-accent)" "textColor" "var(--color-bg)" "icon" "" "iconStyle" "" "title" "Alert")
  "none" (dict "color" "var(--color-bg)" "textColor" "var(--color-text)" "icon" "" "iconStyle" "" "title" "Alert")
-}}
```

`--color-accent`, `--color-bg` and `--color-text` are CSS variables defined in `assets/css/theme.css` that you can override to customize the colors of `ACCENT` and `NONE` styles.

```css {title="assets/css/theme.css"}
/* Theme colors */
:root {
    /* Light theme (default) */
    --color-bg: #fcfcfc;
    --color-text: #222222;
    --color-accent: #01827c;

    /* Dark theme palette */
    --dark-color-bg: #001f2c;
    --dark-color-text: #cad6e2;
    --dark-color-accent: #00fff2;
}
```

> Note: changing `theme.css` variables will affect all components that use those variables.


## Examples

### Example 1: Simple blockquote

```markdown
> "There is no place like home." — Example
```

**Output:**
> "There is no place like home." — Example

### Example 2: Alert blockquote (with default styles)

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

### Example 3: Alert blockquote with custom title, color and icon

```markdown
> [!NONE] Python 3.11 Required
> Make sure to upgrade your Python version to 3.11.
{color="#77a03d" textcolor="#ffffff" icon="python" iconstyle="brands"}
```

**Output:**
> [!NONE] Python 3.11 Required
> Make sure to upgrade your Python version to 3.11.
{color="#77a03d" textcolor="#ffffff" icon="python" iconstyle="brands"}

> **Note**: In this example, we used `NONE` style, but you can use any of the default styles and override their default color and icon as needed (check example below). 

### Example 4: Alert blockquote with overriden attributes

#### Custom Color and Text Color

```markdown
> [!WARNING]
This is a warning with a custom color.
{color="#ff22f0" textcolor="#ffffff"}
```

> [!WARNING]
This is a warning with a custom color and text color.
{color="#ff22f0" textcolor="#ffffff"}

#### Custom Icon

```markdown
> [!INFO]
This is an informational message with a custom icon.
{icon="heart" iconstyle="regular"}
```

> [!INFO]
This is an informational message with a custom icon.
{icon="heart" iconstyle="regular"}

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
