---
title: "Shortcodes: Widgets"
slug: "shortcodes-widgets"
date: 2025-10-29
tags: ["basics", "shortcodes"]
weight: 2

---


## Expand/Collapse

The Table of Contents above is wrapped in an expand/collapse shortcode. Use it on any page to hide long sections or reveal extra details on demand. 

{{< spacing size="xxs" >}}

**Example 1** : Collapsed section with a title
```
{{</* expand title="Click to reveal more" */>}}
... markdown content to be displayed
{{</* /expand */>}}
```

{{< expand title="Click to reveal more" >}}
This content is hidden by default. You can include:

- **Markdown formatting**
- Lists and [links](/guide/markdown_extras#expandcollapse-component)
- Code blocks
- Any other markdown content

```python
def hello():
    print("Hello from inside an expand!")
```

Click the summary again to collapse.
{{< /expand >}}

{{< spacing size="xxs" >}}

**Example 2**: Expanded section with default title
```
{{</* expand open="true" */>}}
... already expanded content
{{</* /expand */>}}
```

{{< expand open="true" >}}
Expand also supports an open param that sets initial state of component,`open = "true"` equals an already expanded component. 

Also, if you don't specify a title, it defaults to "Details".
{{< /expand >}}

## Icon
Insert icons inline within markdown content using the icon shortcode.

{{< spacing size="xxs">}}

**Example 1**: Inserting an icon
```
Here is a star icon: {{</* icon name="star" style="regular" */>}}
``` 

Here is a star icon: {{< icon name="star" style="regular" >}}

{{< spacing size="xxs">}}

**Example 2**: Icon with different size
```
Here is same star icon but filled : {{</* icon name="star" style="solid" */>}}
```

Here is same star icon but filled : {{< icon name="star" style="solid" >}}

{{< spacing size="xxs">}}

> Icons are fetched from [Font Awesome](https://fontawesome.com/icons) free catalog. Check [Regular](https://fontawesome.com/search?ip=classic&s=regular&ic=free-collection), [Solid](https://fontawesome.com/search?ip=classic&s=solid&ic=free-collection) & [Brands](https://fontawesome.com/search?ip=brands&ic=free-collection) collection for a list of suported icons.

## Badge

Display colorful marker badges inline with your text to highlight important information, versions, statuses, or any other metadata.

{{< spacing size="xxs">}}

**Example 1**: Simple badge (avoid using it without proper styling)
```
{{%/* badge */%}}Important{{%/* /badge */%}}
```

{{% badge %}}Important{{% /badge %}}

{{< spacing size="xxs">}}

**Example 2**: Badge with style
```
{{%/* badge style="info" */%}}New{{%/* /badge */%}} 
{{%/* badge style="note" */%}}Note{{%/* /badge */%}} 
{{%/* badge style="tip" */%}}Optional{{%/* /badge */%}} 
{{%/* badge style="warning" */%}}Breaking{{%/* /badge */%}} 
{{%/* badge style="important" */%}}Caveat{{%/* /badge */%}} 
{{%/* badge style="caution" */%}}Don'ts{{%/* /badge */%}}

```

{{% badge style="info" %}}New{{% /badge %}} 
{{% badge style="note" %}}Note{{% /badge %}} 
{{% badge style="tip" %}}Optional{{% /badge %}} 
{{% badge style="warning" %}}Breaking{{% /badge %}}
{{% badge style="important" %}}Caveat{{% /badge %}} 
{{% badge style="caution" %}}Don'ts{{% /badge %}}

{{< spacing size="xxs">}}

**Example 3**: Badge with custom title, color and icon
```
{{%/* badge color="#007bff" textColor="#fff" title="Version" */%}}6.6.6{{%/* /badge */%}}
{{%/* badge color="#dc3545" textColor="#fbff00" icon="angle-double-up" title="Rank" */%}}Captain{{%/* /badge */%}}
```

{{% badge color="#007bff" textColor="#fff" title="Version" %}}6.6.6{{% /badge %}} {{% badge color="#dc3545" textColor="#fbff00" icon="angle-double-up" title="Rank" %}}Captain{{% /badge %}}

{{< spacing size="xxs">}}

**Example 4**: Badge inline with text
```
Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, 
sed quia consequuntur magni dolores eos qui ratione voluptatem sequi 
nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet,
{{%/* badge color="#6ab0de" textColor="#000" icon="rocket" */%}}Awesome{{%/* /badge */%}} 
consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt 
ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima 
veniam, quis nostrum exercitationem ullam corporis suscipit.
```

Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, 
sed quia consequuntur magni dolores eos qui ratione voluptatem sequi 
nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet,
{{% badge color="#6ab0de" textColor="#000" icon="rocket" %}}Awesome{{% /badge %}} 
consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. 
Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit.

{{< spacing size="xxs">}}

> To remove the default icon or title from a severity style (`info`, `note`, `tip`, `warning`, `important`, `error`), set the parameter to `" "` (a space).