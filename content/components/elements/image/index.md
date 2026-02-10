---
title: Images
slug: "images"
date: 2025-10-29
tags: ["elements"]
---

A Simple Image element that is rendered using the HTML `<img>` tag.

<!--more-->

## Features
- Supports tooltip and aria labels using [alt text](#alt-text).
- Supports adding caption using the [title](#title) attribute.
- Supports image resizing using custom [attributes](#attributes).
- Supports [loading images](#image-path) from page resource, site resource or remote URLs.
- Loads all images with `loading="lazy"` attribute for better performance.

## Syntax

The basic syntax for images in Markdown follows this pattern:

```
![alt text](image-path "optional title")
```

{{< spacing size="sm" >}}

Provide additional attributes to images using curly braces after the image syntax:

```
![alt text](image-path "optional title") {width="600" height="400"}
```

### Components
Alt Text
: Provides alternative text for screen readers and displays when image fails to load
: Also used as tooltip text on hover.

Image Path
: An image can be rendered from below three sources:
   - **Page Resource**: Image in the same directory as the markdown file (e.g., `karigurashi002.jpg`)
   - **Site/Global Resource**: Image in the `assets/` directory (e.g., `/images/chihiro043.jpg`)
   - **Remote URL**: Full HTTP/HTTPS URL (e.g., `https://example.com/image.jpg`)
   > [!NOTE]
   > 
   > ```
   > .
   > ├── assets
   > │   └── images
   > │       └── chihiro043.jpg              <-- Image from site/global resource
   > └── content
   >     ├── _index.md
   >     └── advanced
   >         ├── _index.md
   >         ├── elements
   >         │   ├── _index.md
   >         │   ├── image
   >         │   │   ├── index.md            <-- This File
   >         │   │   └── karigurashi002.jpg  <-- Image from page resource 
   >         │   └── image.md
   >         └── shortcodes
   >             └── _index.md
   >```

Title
: Displays as a caption below the image 

Attributes
: Supports setting image's `width` and `height` using hugo's image processing pipeline.

> Refer Hugo's excellent resource on [image processing](https://gohugo.io/content-management/image-processing/) for more details.

## Examples

### Example 1: Image from Page Resource

A simple image:

```markdown
![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg)
```

**Output:**

![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg)



### Example 2: Image With Optional Caption

A simple image with optional caption:

```markdown
![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")
```

**Output:**

![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")

#### Caption Alignment
You can align the caption to `left`, `center`, or `right` using the `captionAlign` attribute:

```markdown
![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")
{captionalign="right"}
```

**Output:**

![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")
{captionalign="right"}

### Example 3: Image with Width and Height

Specify both dimensions for precise control:

```markdown
![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")
{width="300" height="200"}
```

**Output:**

![Studio Ghibli: karigurashi002.jpg](karigurashi002.jpg "Studio Ghibli: Arrietty (2010)")
{width="300" height="160"}


### Example 4: Image from Site Resource

Load an image from the site's `assets/images/` directory:

```markdown
![Studio Ghibli: chihiro043.jpg](images/chihiro043.jpg "Studio Ghibli: Spirited Away (2001)")
```

**Output:**

![Studio Ghibli: Spirited Away](images/chihiro043.jpg "Studio Ghibli: Spirited Away (2001)")


### Example 5: Image from remote URL

You can add any valid HTML attributes:

```markdown
![Studio Ghibli: ged003.jpg](https://www.ghibli.jp/gallery/ged003.jpg "Studio Ghibli: Tales from Earthsea (2006)")
```

**Output:**

![Studio Ghibli: ged003.jpg](https://www.ghibli.jp/gallery/ged003.jpg "Studio Ghibli: Tales from Earthsea (2006)")

### Example 6: Wide Sized Image
Wrap an image in wide partial to make image width extend full width of the viewport.
```markdown
{{</* wide */>}}
![Studio Ghibli: chihiro043.jpg](images/chihiro043.jpg "Studio Ghibli: Spirited Away (2001)")
{captionalign="center"}
{{</* /wide */>}}
```

**Output:**

{{< wide >}}
![Studio Ghibli: Spirited Away](images/chihiro043.jpg "Studio Ghibli: Spirited Away (2001)")
{captionalign="center"}
{{< /wide >}}