---
title: Tables
slug: "tables"
date: 2025-10-29
tags: ["elements"]
---
A standard table element rendered using standard markdown table syntax, with Hugo extensions for captions, header settings, and column alignment.

<!--more-->

## Features
- Supports standard markdown table syntax.
- Supports adding [captions](#example-2-table-with-caption), and [alignment of captions](#caption-alignment) to left, center, or right.
- [Align column](#example-4-table-with-column-text-alignment) text to left, center, right.
- Supports table [header](#example-3-table-with-different-heading-settings) to either be first row, column, both or none.

## Syntax

Basic markdown table syntax:

```
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
```

{{< spacing size="sm" >}}

Provide additional attributes to tables using curly braces after table:

```
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
{caption="A Table Caption" header="row"}
```

{{< spacing size="sm" >}}

[Align](#example-4-table-with-column-text-alignment) text in columns using `:` in header row:

```
| Left Aligned | Center Aligned | Right Aligned |
| :----------- | :------------: | ------------: |
| Cell 1       | Cell 2         | Cell 3        |
```


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

##### Left Aligned Caption (Default)

```markdown
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="left"}
```

**Output:**
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="left"}

##### Center Aligned Caption

```markdown
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="center"}
```

**Output:**
| Movie         | Year |
| ------------- | ---- |
| Totoro        | 1988 |
| Spirited Away | 2001 |
{caption="Studio Ghibli Films" captionalign="center"}

##### Right Aligned Caption

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

#### First Row as Header (Default)

```markdown
| Name    | Role     |
| ------- | -------- |
| Kiki    | Witch    |
| Chihiro | Student  |
{header="column"}
```

**Output:**
| Character | Kiki   | Chihiro |
| --------- | ------ | ------- |
| Movie     | Kiki's Delivery Service | Spirited Away |
| Role      | Witch  | Student |
{header="row"}

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

#### Both First Row and Column as Headers

```markdown
| Character | Kiki   | Chihiro |
| --------- | ------ | ------- |
| Movie     | Kiki's Delivery Service | Spirited Away |
| Role      | Witch  | Student |
{header="both"}
```

**Output:**
| Character | Kiki   | Chihiro |
| --------- | ------ | ------- |
| Movie     | Kiki's Delivery Service | Spirited Away |
| Role      | Witch  | Student |
{header="both"}


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


### Example 6: Really wide table
If you have a table with many columns, it will automatically be horizontally scrollable :
```markdown
| Name    | Role      | Year | Movie                   | Director        | Genre     | Rating | Country | Language | Awards  | Box Office |
| :------ | :-------: | ----:| :---------------------: | :-------------: | :-------: | :----: | :-----: | :------: | :-----: | :--------: |
| Kiki    | Witch     | 1989 | Kiki's Delivery Service | Hayao Miyazaki  | Fantasy   | 7.9    | Japan   | Japanese | None    | $41M       |
| Chihiro | Student   | 2001 | Spirited Away           | Hayao Miyazaki  | Fantasy   | 8.6    | Japan   | Japanese | Oscar   | $355M      |
| Sophie  | Hat Maker | 2004 | Howl's Moving Castle    | Hayao Miyazaki  | Fantasy   | 8.2    | Japan   | Japanese | None    | $236M      |
| Pazu    | Engineer  | 1986 | Castle in the Sky       | Hayao Miyazaki  | Adventure | 8.0    | Japan   | Japanese | None    | $15M       |
```

**Output:**
| Name    | Role      | Year | Movie                   | Director        | Genre     | Rating | Country | Language | Awards  | Box Office |
| :------ | :-------: | ----:| :---------------------: | :-------------: | :-------: | :----: | :-----: | :------: | :-----: | :--------: |
| Kiki    | Witch     | 1989 | Kiki's Delivery Service | Hayao Miyazaki  | Fantasy   | 7.9    | Japan   | Japanese | None    | $41M       |
| Chihiro | Student   | 2001 | Spirited Away           | Hayao Miyazaki  | Fantasy   | 8.6    | Japan   | Japanese | Oscar   | $355M      |
| Sophie  | Hat Maker | 2004 | Howl's Moving Castle    | Hayao Miyazaki  | Fantasy   | 8.2    | Japan   | Japanese | None    | $236M      |
| Pazu    | Engineer  | 1986 | Castle in the Sky       | Hayao Miyazaki  | Adventure | 8.0    | Japan   | Japanese | None    | $15M       |


### Example 7: Wide Sized Table
Or instead wrap such a really wide table in wide partial to make table width extend full width of the viewport.
```markdown
{{</* wide */>}}
| Name    | Role      | Year | Movie                   | Director        | Genre     | Rating | Country | Language | Awards  | Box Office |
| :------ | :-------: | ----:| :---------------------: | :-------------: | :-------: | :----: | :-----: | :------: | :-----: | :--------: |
| Kiki    | Witch     | 1989 | Kiki's Delivery Service | Hayao Miyazaki  | Fantasy   | 7.9    | Japan   | Japanese | None    | $41M       |
| Chihiro | Student   | 2001 | Spirited Away           | Hayao Miyazaki  | Fantasy   | 8.6    | Japan   | Japanese | Oscar   | $355M      |
| Sophie  | Hat Maker | 2004 | Howl's Moving Castle    | Hayao Miyazaki  | Fantasy   | 8.2    | Japan   | Japanese | None    | $236M      |
| Pazu    | Engineer  | 1986 | Castle in the Sky       | Hayao Miyazaki  | Adventure | 8.0    | Japan   | Japanese | None    | $15M       |
{{</* /wide */>}}
```

**Output:**

{{< wide >}}
| Name    | Role      | Year | Movie                   | Director        | Genre     | Rating | Country | Language | Awards  | Box Office |
| :------ | :-------: | ----:| :---------------------: | :-------------: | :-------: | :----: | :-----: | :------: | :-----: | :--------: |
| Kiki    | Witch     | 1989 | Kiki's Delivery Service | Hayao Miyazaki  | Fantasy   | 7.9    | Japan   | Japanese | None    | $41M       |
| Chihiro | Student   | 2001 | Spirited Away           | Hayao Miyazaki  | Fantasy   | 8.6    | Japan   | Japanese | Oscar   | $355M      |
| Sophie  | Hat Maker | 2004 | Howl's Moving Castle    | Hayao Miyazaki  | Fantasy   | 8.2    | Japan   | Japanese | None    | $236M      |
| Pazu    | Engineer  | 1986 | Castle in the Sky       | Hayao Miyazaki  | Adventure | 8.0    | Japan   | Japanese | None    | $15M       |
{{< /wide >}}
