---
title: Codeblocks
slug: "codeblocks"
date: 2025-10-29
tags: ["elements"]
coverLight: "covers/elements/codeblock_light.png"
coverDark: "covers/elements/codeblock_dark.png"
---

A code element rendered using standard markdown codeblock syntax.

<!--more-->

## Features
- Supports standard Markdown codeblock syntax with triple backticks.
- Syntax highlighting for various programming languages.
- Optional line numbers for code readability.
- Copy-to-clipboard functionality for easy code sharing.
- Supports highlighting specific lines or ranges.

## Syntax

Basic codeblock syntax (no syntax highlighting):

````
```
code here
```
````

Syntax highlighted codeblock (specify language after opening backticks):
````
```language
code here
```
````

Syntax highlighted codeblock with attributes :
````
```language {linenos=table hl_lines=["2", "4-5"] showtitle=false showcopy=false title="Example Code"}
code here
```
````

## Parameters
You can specify a variety of options inside curly braces on the opening fence. Common attributes include:

Language
: (optional) Specifies the programming language for syntax highlighting (e.g. `python`, `javascript`, `html`). If you don't specify a language, it will render as a plain code block without syntax highlighting.

Code (that needs to be highlighted)
: The actual code content goes between the opening and closing triple backticks ` ``` `.

Extras
: Below optional attributes that can be added in curly braces after language,

  linenos
  : set to `table` or `inline` to enable line numbers.
  
  hl_lines
  : list of lines or ranges to highlight (e.g. `["2", "4-5"]`).
  
  showtitle
  : `true`/`false` toggle the header/title bar.
  
  showcopy
  : `true`/`false` toggle the copy‑to‑clipboard button.
  
  title
  : custom title text displayed in the header bar.

## Theming
Codeblocks are themed using chroma highlighting, this theme uses following chroma themes for light and dark mode respectively:

- Light mode: `solarized-light`
- Dark mode: `solarized-dark256`

If you have not created it already then create this folder `assets/css/chroma` in your Hugo site and generate custom chroma themes using below command:
```bash
hugo gen chromastyles --style=solarized-light > assets/css/chroma/light.css
hugo gen chromastyles --style=solarized-dark256 > assets/css/chroma/dark.css
```

Replace `solarized-light` and `solarized-dark256` with any other chroma themes of your choice, you can find the full list of available chroma themes here: https://xyproto.github.io/splash/docs/all.html.


## Examples

### Example 1: Simple Codeblock (no syntax highlighting)

````
```
console.log('Hello, World!');
```
````

**Output:**

```
console.log('Hello, World!');
```

### Example 2: Codeblock with Syntax Highlighting

````
```javascript
function greet(name) {
    console.log('Hello, ' + name + '!');
}

greet('Hugo');
```
````

**Output:**

```javascript
function greet(name) {
    console.log('Hello, ' + name + '!');
}

greet('Hugo');
```

### Example 3: Codeblock with Line Numbers

#### Table Style Line Numbers (Default)

````
```python {linenos=table}
def add(a, b):
    return a + b
```
````

**Output:**

```python {linenos=table}
def add(a, b):
    return a + b
```

#### Inline Line Numbers

````
```python {linenos=inline}
def add(a, b):
    return a + b
```
````  

**Output:**

```python {linenos=inline}
def add(a, b):
    return a + b
``` 

### Example 4: Codeblock with Highlighted Lines

````
```python {hl_lines=["2", "4-5"]}
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```
````

**Output:**

```python {hl_lines=["2", "4-5"]}
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
``` 

#### Example 5: Code block with Hidden Elements

##### Hidden Title

Hide the codeblock header/title:

````
```python {showtitle=false}
def add(a, b):
  return a + b
```
````

**Output:**

```python {showtitle=false}
def add(a, b):
  return a + b
```

##### Hidden Copy Button

Hide the copy-to-clipboard button:

````
```python {showcopy=false}
def add(a, b):
  return a + b
```
````

**Output:**

```python {showcopy=false}
def add(a, b):
  return a + b
```

##### Hidden Title and Copy Button

````
```python {showtitle=false showcopy=false}
def add(a, b):
  return a + b
```
````

**Output:**

```python {showtitle=false showcopy=false}
def add(a, b):
  return a + b
```



### Example 6: Codeblock with Custom Title

Set a custom codeblock title:

````
```python {title="main.py"}
def add(a, b):
  return a + b
```
````

**Output:**

```python {title="main.py"}
def add(a, b):
  return a + b
```

### Example 7: A Wide Codeblock

Wrap a codeblock in wide partial to extend the width:

````
{{</* wide */>}}
```json
{
  "name": "freedom-demo",
  "version": "1.0.0",
  "description": "A Hugo theme demo site",
  "main": "index.js",
  "scripts": {
    "build": "hugo",
    "serve": "hugo server -D"
  },
  "dependencies": {
    "hugo": "^0.101.0"
  }
}
```
{{</* /wide */>}}
````

**Output:**

{{< wide >}}
```json
{
  "name": "freedom-demo",
  "version": "1.0.0",
  "description": "A Hugo theme demo site",
  "main": "index.js",
  "scripts": {
    "build": "hugo",
    "serve": "hugo server -D"
  },
  "dependencies": {
    "hugo": "^0.101.0"
  }
}
```
{{< /wide >}}
