---
title: "Markdown Syntax"
slug: "markdown-syntax"
date: 2025-10-29
tags: ["basics"]
weight: 1
---

A comprehensive guide to markdown syntax supported by theme. Each element works out-of-the-box for both dark and light mode.


## Headings

Headings are created using `#` prefixes, with the number of hashes corresponding to the heading level (HTML `<h1>` through `<h6>`).

Also, when you hover over a heading, a {{< icon name="link" >}} sign would appear next to it, you can click on it to go to anchor link of that heading (*this does not copy link, you still have to copy it from address bar*)


```
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

... which is rendered as:

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

> [!TIP]
> Although using a single-hash heading (`#`) to create an H1 is allowed, it's discouraged because the page title is already rendered as an H1, which makes it difficult to distinguish the page title from other headings.


## Text Formatting

### Inline Styles
| Syntax            | Rendering                         |
| ------------------| ----------------------------------|
| `**bold**`        | line with **bold** element        |
| `*italic*`        | line with *italic* element        |
| `` `code` ``      | line with `code` element          |
| `~~deleted~~`     | line with ~~deleted~~ element     |
| `++added++`       | line with ++added++ element       |
| `==mark==`        | line with ==mark== element        |
| `Sub~script~`     | line with Sub~script~ element     |
| `Super^script^`   | line with Super^script^ element   |

> [!NOTE]
> While **bold**, *italic*, `code`, Sub~script~ and Super^script^ works out of the box, you need to add below config to `hugo.yaml` to be able to render ~~deleted~~, ++added++ and ==mark== elements.
> ```yaml
> markup:
>  _merge: shallow
> ```


### Line Spacing

#### New Paragraph

Leaving a blank line between two lines, creates a new paragraph, this adds more spacing between those lines.

```
Paragraph 1

Paragraph 2
```

... which is rendered as:

Paragraph 1

Paragraph 2

#### Line Break

A line break (by adding 2 extra spaces at end of line) does not create a new para but just adds a `<br>` element between them, this adds less spacing between those lines. 

```
Paragraph 1  
Still Paragraph 1
```

... which is rendered as:

Paragraph 1  
Still Paragraph 1

> If you don't like theme's spacing between 2 components, try exploring [spacing](/guide/markdown-extras#spacing-shortcode).

## Links

### Automatic Links

**Clickable URL**:
| Syntax      | `https://example.com` |
| ----------- | --------------------- |
| Rendering   | https://example.com   |
{header="column"}

**Non-clickable (using code):**
| Syntax      | `` `https://example.com` `` |
| ----------- | --------------------- |
| Rendering   | `https://example.com`   |
{header="column"}

### Custom Text Links



**External link**:  
| Syntax      | `[example](https://example.com)` |
| ----------- | --------------------- |
| Rendering   | [example](https://example.com)   |
{header="column"}

**Internal link**:  
| Syntax      | `[Markdown Syntax](/usage/markdown_syntax/)` |
| ----------- | --------------------- |
| Rendering   | [Markdown Syntax](/usage/markdown_syntax/)   |
{header="column"}

**Anchor link**:

| Syntax      | `[Markdown Syntax > Links](/usage/markdown_syntax#links)` |
| ----------- | --------------------- |
| Rendering   | [Markdown Syntax > Links](/usage/markdown_syntax#links)   |
{header="column"}


### Footnotes

**Footnote reference**:  
| Syntax      | `Text with Footnote [^1]` |
| ----------- | --------------------- |
| Rendering   | Text with Footnote [^1]   |
{header="column"}

> Above footnote link should be paired with actual footnote message  
> 
> {{< spacing size="md" type="horizontal" >}} `[^1]: Sample footnote message.`  
> 
> preferably added at the end of post (irrespective of where you add the message, it would always be rendered at end of post).

## Lists

### Ordered Lists

```
1. Ordered List Item 1
2. Ordered List Item 2
3. Ordered List Item 3
   1. Ordered Sub-List Item 1
```

... which is rendered as:

1. Ordered List Item 1
2. Ordered List Item 2
3. Ordered List Item 3
   1. Ordered Sub-List Item 1

### Unordered Lists

```
- Unordered List Item 1
- Unordered List Item 2
- Unordered List Item 3
  - Unordered Sub-List Item 1
```

... which is rendered as:

- Unordered List Item 1
- Unordered List Item 2
- Unordered List Item 3
  - Unordered Sub-List Item 1

### Task Lists

```
- [X] Checked Task
- [ ] Unchecked Task
```

... which is rendered as:

- [X] Checked Task
- [ ] Unchecked Task

### Definition Lists

```
Term
: Definition 1
: Definition 2
```

... which is rendered as:

Term
: Definition 1
: Definition 2

> [!TIP]
> Definition terms automatically get IDs (similar to headings), allowing you to link directly to them using anchor links.  
> 
> The ID is generated from the term text (e.g., "API Documentation" becomes `#api-documentation`).

## Blockquotes

A blockquote is created by starting a line with `>` :

```
> This is a blockquote.
```

... which is rendered as:

> This is a blockquote.

### Alert Blockquotes

Alert blockquotes help highlight important information using distinct styles. 

Use the following syntax:

```
> [!NOTE]
> Useful information that users should know, even when skimming content.
```

Replace `NOTE` in above syntax with one of the following types to get different styles:
- `INFO` [ {{< icon name="info-circle" style="solid" >}} ]
- `NOTE` [ {{< icon name="info-circle" style="solid" >}} ]
- `TIP` [ {{< icon name="lightbulb" style="solid" >}} ]
- `IMPORTANT` [ {{< icon name="star" style="solid" >}} ]
- `WARNING` [ {{< icon name="circle-exclamation" style="solid" >}} ]
- `CAUTION` [ {{< icon name="triangle-exclamation" style="solid" >}} ]

> [!INFO]
> Useful information that users should know, even when skimming content.

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.


## Horizontal Rule

You can use asterisks (`***`), dashes (`---`), or underscores (`___`) to create a horizontal line:

---

## Images

**Example 1**: A Plain Image

```
![alt text](path/to/image.jpg)
```

... which is rendered as:

![Studio Ghubli: chihiro043](images/chihiro043.jpg)

**Example 2**: An Image with Caption

```
![alt text](path/to/image.jpg "Image Caption")
```

... which is rendered as:

![Studio Ghubli: chihiro043](images/chihiro043.jpg "Image Caption")

> For more advanced image rendering options, refer to [Image Element](/components/elements/images/).

## Tables

**Example 1**: A simple Table
```
| Movie         | Year |
| ------------- | ---- |
| My Neighbor Totoro | 1988 |
| Spirited Away | 2001 |
```

**Example 2**: A Table with caption
```
| Movie         | Director       |
| ------------- | -------------- |
| My Neighbor Totoro | Hayao Miyazaki |
| Spirited Away | Hayao Miyazaki |
{caption="Studio Ghibli Films"}
```
... which is rendered as :

| Movie         | Director       |
| ------------- | -------------- |
| My Neighbor Totoro | Hayao Miyazaki |
| Spirited Away | Hayao Miyazaki |
{caption="Studio Ghibli Films"}


> For more advanced image rendering options, refer to [Table Element](/components/elements/tables/).

## Code Blocks

### Plain Multi-line Code Block

Surround code with triple backticks:

````
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```
````

... which is rendered as :
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```

### Syntax-Highlighted Code Block

Add the language name after the opening backticks:

````
```json
{
    "syntax": "Header",
    "description": "Title"
}
```
````

... which is rendered as:

```json
{
    "syntax": "Header",
    "description": "Title"
}
```

[^1]: Sample footnote message.