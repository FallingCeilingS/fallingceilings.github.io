---
title: HD solution in mobile terminal
date: 2020-09-19 17:34:03
mathjax: true
tags:
- front-end brief
- css
---

{% katex %}
DPR \textrm{(device pixel ratio)} = \textrm{Device Pixel} / \textrm{CSS Pixel}
{% endkatex %}

### **1px solution**

- `border-image`, `background-image` - disadvantages: it is troublesome to modify colour, and rounded corner needs special handling.
- `box-shadow` - disadvantage: Safari doesn't support decimal parameter value.
- Pseudo class and `transform`.
- SVG.
- Viewport and `rem`.
