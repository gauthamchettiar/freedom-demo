---
title: "Theme Customization"
slug: "theme-customization"
date: 2025-10-29
tags: ["basics"]
weight: 4
---

Theme can be customized in a bunch of ways, from simpler CSS overrides to more advanced hugo template overrides. Below are some of the most common ways to customize the theme.

## theme.css override
The simplest way to customize the theme is to override `assets/css/theme.css` file.

```css {title="assets/css/theme.css"}
/* Theme colors */
:root {
    /* Light theme (default) */
    --color-bg: #fcfcfc;
    --color-text: #222222;
    --color-link: #0000ee;
    --color-accent: #01827c;

    /* Dark theme palette */
    --dark-color-bg: #001f2c;
    --dark-color-text: #cad6e2;
    --dark-color-link: #6b9eff;
    --dark-color-accent: #00fff2;

    /* 
       this actually has a lot more variables, 
       it has been truncated for brevity 
    */
}
```

> Note: You need to copy complete `theme.css` file to your site's `assets/css/theme.css` to override the default theme variables. You can then modify the variables as needed to customize the theme's colors, fonts, spacing and layout.

### All Supported CSS Variables

| Variable Name | Mode | Description |
| --- | --- | --- |
| `--color-bg` | {{< icon name="sun" >}} | Primary background color (light theme) |
| `--color-text` | {{< icon name="sun" >}} | Default text color |
| `--color-link` | {{< icon name="sun" >}} | Color used for hyperlinks |
| `--color-accent` | {{< icon name="sun" >}} | Accent color used across theme. |
| `--color-h1` | {{< icon name="sun" >}} | Color for `<h1>` headings |
| `--color-h2` | {{< icon name="sun" >}} | Color for `<h2>` headings |
| `--color-h3` | {{< icon name="sun" >}} | Color for `<h3>` headings |
| `--color-h4` | {{< icon name="sun" >}} | Color for `<h4>` headings |
| `--color-h5` | {{< icon name="sun" >}} | Color for `<h5>` headings |
| `--color-h6` | {{< icon name="sun" >}} | Color for `<h6>` headings |
| `--color-mark` | {{< icon name="sun" >}} | Color used for `<mark>` and other highlights |
| `--dark-color-bg` | {{< icon name="moon" >}} | Background color for dark theme |
| `--dark-color-text` | {{< icon name="moon" >}} | Text color for dark theme |
| `--dark-color-link` | {{< icon name="moon" >}} | Link color for dark theme |
| `--dark-color-accent` | {{< icon name="moon" >}} | Accent color for dark theme |
| `--dark-color-h1` | {{< icon name="moon" >}} | `<h1>` color in dark theme |
| `--dark-color-h2` | {{< icon name="moon" >}} | `<h2>` color in dark theme |
| `--dark-color-h3` | {{< icon name="moon" >}} | `<h3>` color in dark theme |
| `--dark-color-h4` | {{< icon name="moon" >}} | `<h4>` color in dark theme |
| `--dark-color-h5` | {{< icon name="moon" >}} | `<h5>` color in dark theme |
| `--dark-color-h6` | {{< icon name="moon" >}} | `<h6>` color in dark theme |
| `--dark-color-mark` | {{< icon name="moon" >}} | Highlight color for dark theme |
| `--font-body` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Font family for body text |
| `--font-header` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Font family used in headings |
| `--font-code` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Font family for code blocks and inline code |
| `--spacing-xxs` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Extra‑extra‑small spacing value |
| `--spacing-xs` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Extra‑small spacing value |
| `--spacing-sm` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Small spacing value |
| `--spacing-md` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Medium spacing value |
| `--spacing-lg` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Large spacing value |
| `--spacing-xl` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Extra‑large spacing value |
| `--spacing-xxl` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Extra‑extra‑large spacing value |
| `--page-width` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Maximum width for content area |
| `--line-height` | {{< icon name="sun" >}}/{{< icon name="moon" >}} | Default line height for text |


## Default Style Overrides
Certain components like [alerts](/components/elements/blockquotes#example-2-alert-blockquote-with-default-styles), and shortcodes like mark, and badges use default styles that are defined in `alert-styles.html`. You can override these styles by copying the file to your site's `layouts/_partials/utils/alert-styles.html` and modifying the styles as needed.

```go-html-template {title="layouts/_partials/utils/alert-styles.html"}
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

`--color-accent`, `--color-bg` and `--color-text` are CSS variables defined in [`assets/css/theme.css`](#themecss-override).

##  Default Chroma Syntax Highlighting Styles
Codeblocks are themed using chroma highlighting, this theme uses following chroma themes for light and dark mode respectively:

- Light mode: `solarized-light`
- Dark mode: `solarized-dark256`

If you have not created it already then create this folder `assets/css/chroma` in your Hugo site and generate custom chroma themes using below command:
```bash
hugo gen chromastyles --style=solarized-light > assets/css/chroma/light.css
hugo gen chromastyles --style=solarized-dark256 > assets/css/chroma/dark.css
```

Replace `solarized-light` and `solarized-dark256` with any other chroma themes of your choice, you can find the full list of available chroma themes here: https://xyproto.github.io/splash/docs/all.html.


## Custom Layouts Supported
This theme supports following custom layouts that you can use by adding `layout: <layout-name>` in front matter of your content files.

| Layout Name | File Location | Description |
| --- | --- | --- |
| home | `layouts/home.html` | Custom layout for [homepage](/), this is applied by default to file at `content/_index.md` |
| section | `layouts/section.html` | Custom layout for [section list](/guide/) pages, this page is used to list all of its subpages. This is applied by default to all nested `_index.md` files except the one at root (i.e: `content/_index.md`) |
| page | `layouts/page.html` | Custom layout for regular pages, this is applied by default to all content files (i.e: any file which is not `_index.md`) |
| taxonomy | `layouts/taxonomy.html` | Custom layout for [taxonomy list](/tags/) pages, this is applied by default to all taxonomy list pages (e.g. `/tags/`). This is autogenerated, you do not need to add any md files for it |
| term | `layouts/term.html` | Custom layout for [taxonomy term](/tags/basics/) pages, this is applied by default to all taxonomy term pages (e.g. `/tags/guides/`). This is autogenerated, you do not need to add any md files for it |
| archive | `layouts/archive.html` | Custom layout for [archive page](/archive/) (page with all posts listed by year), this is autogenerated, you do not need to add any md files for it |

```
└── content
    ├── _index.md                        -- home page
    ├── components
    │   ├── _index.md                    -- section page (for components section)
    │   ├── elements
    │   │   ├── _index.md                -- section page (for elements section)
    │   │   ├── blockquote.md            -- regular page (for blockquote component)
    │   │   ├── image
    │   │   │   ├── index.md             -- regular page (for image component)
    │   │   │   └── karigurashi002.jpg
    │   │   └── table.md                 -- regular page (for table component)
    │   └── shortcodes
    │       ├── _index.md                -- section page (for shortcodes section)
    │       └── icons.md                 -- regular page (for icons shortcode)
    └── guide
        ├── _index.md                    -- section page (for guide section)
        ├── theme_customization.md       -- regular page (for theme customization guide)
        └── widgets.md                   -- regular page (for widgets guide)
```

### Special Layouts
In addition to above layouts, there are few special layouts that you can use for specific use cases. These layouts are not applied by default to any content files, you need to explicitly add `layout: <layout-name>` in front matter to use them.

| Layout Name | File Location | Description |
| --- | --- | --- |
| Content Only | `layouts/_default/content_only.html` | A minimal layout that only renders content (will still have header and footer). You can use this layout by adding `layout: content_only` in front matter of your content file. |
| Content with Breadcrumbs | `layouts/_default/content_with_breadcrumbs.html` | Similar to Content Only but also includes breadcrumbs navigation at the top. You can use this layout by adding `layout: content_with_breadcrumbs` in front matter of your content file. |
| List Card | `layouts/_default/list_card.html` | A custom layout for section pages that renders content in a card style layout (default in section is list style layout). You can use this layout by adding `layout: list_card` in front matter of your section's `_index.md` file. |