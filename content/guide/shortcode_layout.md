---
title: "Shortcodes: Layouts"
slug: "shortcodes-layouts"
date: 2025-10-29
tags: ["basics", "shortcodes"]
weight: 4

---


## Wide
By default all elements are contained within page-width, use the wide shortcode to make them span full width of the viewport.

This is supported for [images](/guide/markdown_syntax#images), [tables](/guide/markdown_syntax#tables), [alert blockquotes](http://localhost:1313/guide/markdown-syntax/#alert-blockquotes), [code blocks](http://localhost:1313/guide/markdown-syntax/#code-blocks), [paragraphs](/guide/markdown_syntax#paragraphs), and any other html elements.


{{< spacing size="xxs" >}}

**Example**: Wide Image

```
{{</* wide */>}}
![chihiro043](images/chihiro043.jpg)
{{</* /wide */>}}
```

{{< wide >}}
![chihiro043](images/chihiro043.jpg)
{{< /wide >}}


## Full
If an image or table has width smaller than page width, they would be left aligned and not span full width. Use the full shortcode to make them span full width of the container even if their natural width is smaller.

This is supported for [images](/guide/markdown_syntax#images) (whose width is smaller than page width), and [tables](/guide/markdown_syntax#tables).

{{< spacing size="xxs" >}}

**Example**: Full Width Table 

```
{{</* full */>}}
| Movie         | Year |
| ------------- | ---- |
| My Neighbor Totoro | 1988 |
| Spirited Away | 2001 |
{{</* /full */>}}
```

{{< full >}}
| Movie         | Year |
| ------------- | ---- |
| My Neighbor Totoro | 1988 |
| Spirited Away | 2001 |
{{< /full >}}


## Spacing
Theme by default does not provide distinguishable spacing between elements, so use this shortcode to add spacing where needed.

{{< spacing size="sm" >}}

A **vertical spacing** can be added between elements using *`{{</* spacing size="lg" */>}}`*

This text has spacing below ↓
{{< spacing size="lg" >}}
This text has spacing above ↑

{{< spacing size="sm" >}}

Below text has **horizontal spacing** between Left and Right inline elements using *`{{</* spacing size="xxl" type="horizontal" */>}}`*

Left → {{< spacing size="xxl" type="horizontal" >}} ← Right

{{< spacing size="xxs">}}

> Sizes supported are: ++`xxs`++, ++`xs`++, ++`sm`++, ++`md`++, ++`lg`++, ++`xl`++, ++`xxl`++


## Alignment

Align content to the `left`, `center`, or `right`:

**Example 1**: Content aligned to left
```
{{</* align align="left" */>}}
This paragraph is aligned to the left.
{{</* /align */>}}
```

{{< align align="left" >}}
This paragraph is aligned to the left.
{{< /align >}}

**Example 2**: Content aligned to center
```
{{</* align align="center" */>}}
This paragraph is centered.
{{</* /align */>}}
```

{{< align align="center" >}}
This paragraph is centered.
{{< /align >}}

**Example 3**: Content aligned to right
```
{{</* align align="right" */>}}
This paragraph is aligned to the right.
{{</* /align */>}}
```

{{< align align="right" >}}
This paragraph is aligned to the right.
{{< /align >}}

This works with any element that has width less than container width like [tables](/guide/markdown_syntax#tables):


{{< align align="center" >}}
| Syntax      | Description                         |
| ----------- | ----------------------------------- |
| Header      | This is description of header       |
| Paragraph   | This is description of Paragraph    |
{caption="A Center Aligned Table"}
{{< /align >}}
