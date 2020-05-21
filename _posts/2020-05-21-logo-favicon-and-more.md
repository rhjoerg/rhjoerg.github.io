---
layout: post
title:  "Logo, Favicon and more"
date:     2020-05-21
modified: 2020-05-21
categories: svg
excerpt: Every site needs its `favicon.ico`, every menu item in an application needs its icon, every ... needs its ... image.
---

Every site needs its `favicon.ico`, every menu item in an application needs its icon, every ... needs its ... image.

## The Experiment

As I am not very talented with painting something, I decided to create these items programmatically. I carefully created
an SVG image, rendered it using Apache Batik, and stored the resulting `.png` files.

The current SVG code is shown at [the end](#the-promised-svg) of this post. It isn't embedded yet in this page directly, as it uses a font-family
not available on all platforms.

But I show you the rendered images at different sizes:

| 128 x 128 | 64 x 64 | 48 x 48 | 32 x 32 | 24 x 24 | 16 x 16 |
| --- | --- | --- | --- | --- | --- |
| ![Logo at 128 pixels][logo-128] | ![Logo at 64 pixels][logo-64] | ![Logo at 48 pixels][logo-48] | ![Logo at 32 pixels][logo-32] | ![Logo at 24 pixels][logo-24] | ![Logo at 16 pixels][logo-16] |

Starting at size 32, the result looks suspicous. Let's zoom in:

| 32 x 32 | 24 x 24 | 16 x 16 |
| --- | --- | --- |
| <img alt="Zoomed-in 32px logo" src="/assets/screwed-logos/logo@32.png" width="128" /> | <img alt="Zoomed-in 24px logo" src="/assets/screwed-logos/logo@24.png" width="128" /> | <img alt="Zoomed-in 16px logo" src="/assets/screwed-logos/logo@16.png" width="128" /> |

I (not so) proudly declare this experiment as **fail**.

## The promised SVG:

```xml
<svg xmlns="http://www.w3.org/2000/svg" width="256" height="256">
  <rect x="0.0" y="0.0" width="256.0" height="256.0" rx="80.0" ry="80.0" fill="#191970"/>
  <text x="31.0" y="188.0" style="font-family: Consolas;
      font-size: 184px; font-weight: 500; fill: #fff;">RJ</text>
</svg>
```

[logo-128]: /assets/screwed-logos/logo@128.png
[logo-64]: /assets/screwed-logos/logo@64.png
[logo-48]: /assets/screwed-logos/logo@48.png
[logo-32]: /assets/screwed-logos/logo@32.png
[logo-24]: /assets/screwed-logos/logo@24.png
[logo-16]: /assets/screwed-logos/logo@16.png

