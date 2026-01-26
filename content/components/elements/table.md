---
title: Tables
slug: "tables"
date: 2025-10-29
tags: ["elements"]
---
A standard table element rendered using standard Markdown table syntax, with Hugo extensions for captions, header settings, and column alignment.

<!--more-->

## Features
- Supports standard Markdown table syntax.
- Add captions using `{caption="..."}` after the table.
- Control header rendering with `{header="row"}`, `{header="column"}`, or `{header="none"}`.
- Align column text (left, center, right) using `:` in the header row.
- Heading background styling follows theme accent color (`--color-accent`).
- Responsive and accessible.

## Syntax

Basic Markdown table syntax:

```
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
```

Add a caption or change header settings using curly braces after the table:

```
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
{caption="A Table Caption" header="row"}
```

Align columns using colons in the separator row:
- `:---` (left), `:---:` (center), `---:` (right)

## Examples

### Example 1: Simple Table

```markdown
| Name    | Role     |
| ------- | -------- |
| Kiki    | Witch    |
| Chihiro | Student  |
```

**Output:**

| Name    | Role     |
| ------- | -------- |
| Kiki    | Witch    |
| Chihiro | Student  |


### Example 2: Table with Caption

```markdown
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films"}
```

**Output:**

| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films"}

#### Caption Alignment

You can align the caption to `left`, `center`, or `right` using the `captionalign` attribute:

```markdown
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="right"}
```

**Output:**

| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="right"}


### Example 3: Table with Different Heading Settings

#### No Header Row

```markdown
| Name    | Role     |
| ------- | -------- |
| Kiki    | Witch    |
| Chihiro | Student  |
{header="none"}
```

**Output:**

| Name    | Role     |
| ------- | -------- |
| Kiki    | Witch    |
| Chihiro | Student  |
{header="none"}

#### First Column as Header

```markdown
| Character | Kiki   | Chihiro |
| --------- | ------ | ------- |
| Movie     | Kiki's Delivery Service | Spirited Away |
| Role      | Witch  | Student |
{header="column"}
```

**Output:**

| Character | Kiki   | Chihiro |
| --------- | ------ | ------- |
| Movie     | Kiki's Delivery Service | Spirited Away |
| Role      | Witch  | Student |
{header="column"}


### Example 4: Table with Column Text Alignment

```markdown
| Name    | Role     |
| :-----: | :------: |
| Kiki    | Witch    |
| Chihiro | Student  |
```

**Output:**

| Name    | Role     |
| :-----: | :------: |
| Kiki    | Witch    |
| Chihiro | Student  |

#### Mixed Alignment

```markdown
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |
```

**Output:**
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |

### Example 5: Full Sized Table 
Wrap a table in full partial to make table width extend full width of the page.
```markdown
{{</* full */>}}
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |
{{</* /full */>}}
```

**Output:**

{{< full >}}
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |
{{< /full >}}

### Example 6: Wide Sized Table
Wrap a table in wide partial to make table width extend full width of the viewport.
```markdown
{{</* wide */>}}
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |
{{</* /wide */>}}
```

**Output:**

{{< wide >}}
| Name    | Role     | Year |
| :------ | :------: | -----: |
| Kiki    | Witch    | 1989 |
| Chihiro | Student  | 2001 |
{{< /wide >}}
