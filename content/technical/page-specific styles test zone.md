---
title: page-specific styles test zone
draft: false
tags:
---

here is a directory of page-specific styling tests!

it's possible to add specific css to pages by adding `[data-slug=""]` to  `quartz/styles/custom.scss`. 

for example, if you want to change the color of the text on link hovers on this page, AND override default CSS stylings:

`quartz/styles/custom.scss`

```ts
[data-slug="page-specific-styles-test-zone"] a:hover { color: purple !important; } ```

