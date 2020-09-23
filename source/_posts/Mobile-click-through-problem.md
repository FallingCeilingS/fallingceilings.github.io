---
title: Mobile click through problem
date: 2020-09-23 21:15:45
tags:
  - front-end brief
  - mobile
---

### **Scenario**

An upper element `A` is bound with `tap` event and element `B` is behind `A`. `B` is bound with `click` event. When we click `A`, `A` will be hidden, and the `click` event of the `B` element will be triggered.
The reason is that `click` event will be triggered after the touch end when the `tap` event of upper layer `A` occurs. Actually, the triggering sequence of these events is `touchstart` - `touchmove` - `touch` - `click`. When the `tap` event triggers within `300ms`, `A` has disappeared, and the real `click` is occurred to the lower layer `B` element. Thus, click through problem will occur.

### **Solutions**

- Use `click` or `tap` for both elements.
- Use `e.preventdefault()` to avoid triggering `click` or `tap` event to the lower layer element in the `touchend` event in the upper layer element.
- Use `FastClick`. `Fastclick` is a library dedicated to solve the `300ms` `click` event delay problem.

### **The principle of `FastClick`**

`document.body` binds `touchstart` and `touchend` events. `touchstart` is to record `targetElement`, that is, the element currently clicked. Then, `touchend` event blocks default event (the `click` events in elements behind). Afterwards, it composes a new `click` event and adds `tracedTouchEvent` property, which is able to be traced. Finally, the new `click` event on `targetElement` is triggered. As a result, the binding function on `targetElement` is executed immediately and `FastClick` procedure is completed.
