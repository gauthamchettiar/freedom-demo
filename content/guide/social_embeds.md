---
title: "Social Embeds"
slug: "social-embeds"
date: 2025-10-29
tags: ["basics"]
weight: 3
---

Hugo provides a set of embedded shortcodes to help you add rich content to your Markdown files without writing raw HTML. These shortcodes work out-of-the-box.

## YouTube

Embed a YouTube video by providing the video ID (Hint: The video ID is the string after `v=` in the YouTube URL).

**Example**: For video https://www.youtube.com/watch?v=w7Ft2ymGmfc

```html
{{</* youtube w7Ft2ymGmfc */>}}
```

**Output**

{{< youtube w7Ft2ymGmfc >}}

> Check [hugo | shortcodes | youtube](https://gohugo.io/shortcodes/youtube/) for more details.

## Vimeo

Embed a Vimeo video by providing the video ID (Hint: The video ID is the string of numbers at the end of the Vimeo URL).

**Example** : For video https://vimeo.com/146022717?fl=pl&fe=vl

```html
{{/*    */}}
{{</* vimeo 146022717 */>}}
```

**Output**

{{< vimeo 146022717 >}}

> Check [hugo | shortcodes | vimeo](https://gohugo.io/shortcodes/vimeo/) for more details.

## X (Tweet)

Embed a tweet by providing the username and tweet ID (Hint: The tweet ID is the long number at the end of the tweet URL).

> **Note:** The `tweet` shortcode might require privacy settings adjustments depending on the user's browser context.

**Example** : For tweet https://twitter.com/SanDiegoZoo/status/1453110110599868418

```html
{{</* x user="SanDiegoZoo" id="1453110110599868418" */>}}
```

**Output**

{{< x user="SanDiegoZoo" id="1453110110599868418" >}}

> Check [hugo | shortcodes | x](https://gohugo.io/shortcodes/x/) for more details.

## Instagram

Embed an Instagram post.

**Example**: for post https://www.instagram.com/p/CJMFOb3jkrT/

```html
{{</* instagram CJMFOb3jkrT */>}}
```
**Output**

{{< instagram CJMFOb3jkrT >}}

> Check [hugo | shortcodes | instagram](https://gohugo.io/shortcodes/instagram/) for more details.