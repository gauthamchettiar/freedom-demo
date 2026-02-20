---
title: Headings
slug: "headings"
date: 2025-10-29
tags: ["elements"]
coverLight: "covers/elements/heading_light.png"
coverDark: "covers/elements/heading_dark.png"
excludefromtoc: ["Heading 1", "Heading 2", "Heading 3", "Heading 4", "Heading 5", "Heading 6"]
---

A standard heading element rendered using Markdown syntax.

<!--more-->

## Features
- Supports standard Markdown heading syntax using `#` for levels 1-6.
- Automatically generates anchor links for easy sharing and navigation.
- Has distinct customizable sizing and colour for each heading level.

## Syntax
Headings are created using `#` prefixes, with the number of hashes corresponding to the heading level (HTML `<h1>` through `<h6>`).

```
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

## Theming
Each heading level has distinct default styling for color and font, which can be customized by overriding `theme.css` variables:

```css {title="assets/css/theme.css"}
/* Theme colors */
:root {
    /* Heading colors */
    --color-h1: #1a1a1a;
    --color-h2: #2c3e50;
    --color-h3: #34495e;
    --color-h4: #546e7a;
    --color-h5: #607d8b;
    --color-h6: #78909c;

    /* Dark heading colors */
    --dark-color-h1: #e8f4f8;
    --dark-color-h2: #b3d9f2;
    --dark-color-h3: #8ec5e8;
    --dark-color-h4: #6db1de;
    --dark-color-h5: #5a9dd1;
    --dark-color-h6: #4a89c4;

    /* Font families */
    --font-header: 'Verdana', 'Arial';
}

@media (prefers-color-scheme: dark) {
    :root {
        --color-bg: var(--dark-color-bg);
        --color-text: var(--dark-color-text);
        --color-link: var(--dark-color-link);
        --color-accent: var(--dark-color-accent);
        --color-h1: var(--dark-color-h1);
        --color-h2: var(--dark-color-h2);
        --color-h3: var(--dark-color-h3);
        --color-h4: var(--dark-color-h4);
        --color-h5: var(--dark-color-h5);
        --color-h6: var(--dark-color-h6);
        --color-mark: var(--dark-color-mark);
    }
}
```

If you don't already have it, create a `theme.css` file in your `assets/css/` directory and add the above CSS variables to customize heading colors. 

Additionally you can customize other attributes like font size, weight, spacing etc. by targeting the heading tags (`h1` to `h6`) in your custom CSS placed in `assets/css/override.css`.

```css {title="assets/css/override.css"}
h1 {
    font-size: 2.5em;
    font-weight: bold;
    margin-bottom: 0.5em;
}

h2 { ... }
h3 { ... }
/* and so on for h4, h5, h6 */
```

## Example

### Example 1: Basic Headings
```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

# Heading 1 
## Heading 2 
### Heading 3 
#### Heading 4 
##### Heading 5 
###### Heading 6 

If you are on a desktop, hover over any heading to see a `{{< icon name="link" >}}` icon appear next to it. Click the icon to navigate to the anchor link for that heading.

If you are on a mobile device, you can tap on empty space next to heading to see a `{{< icon name="link" >}}` icon appear, which you can tap to navigate to the anchor link for that heading.

> Note: The anchor link feature does not copy link to clipboard, you will need to copy it from the address bar after clicking the icon.

### Example 2: Hide Headings from Table of Contents
You can hide specific headings from the Table of Contents by adding their text to the `excludefromtoc` parameter in the page front matter. For example, the following front matter will exclude all standard heading levels from the Table of Contents:

```yaml
# ...
excludefromtoc: ["Heading 1", "Heading 2", "Heading 3", "Heading 4", "Heading 5", "Heading 6"]
```

All headings in the above [example](#example-basic-headings) are hidden from the Table of Contents, but they are still rendered as normal headings in the content.