---
layout: post
title: "A clean way to debounce in JavaScript"
subtitle: "No lodash required"
categories: [code]
---

Debouncing is one of those utilities that's small enough to just write
yourself, but I still see projects pulling in an entire utility library
for it. Here's the version I keep copy-pasting into new projects:

```js
function debounce(fn, delay = 300) {
  let timeoutId;

  return function debounced(...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  };
}
```

Usage looks like this:

```js
const onResize = debounce(() => {
  console.log("window resized to", window.innerWidth);
}, 200);

window.addEventListener("resize", onResize);
```

## Why this version and not a fancier one

A lot of debounce implementations try to also support `leading`/`trailing`
options, cancellation, and `maxWait`. Those are genuinely useful in a
general-purpose library, but for the 95% case — "don't run this expensive
thing on every keystroke" — the eight lines above are enough, and they're
easy enough to read that you don't need to trust a black box.

If you do need cancellation (say, a search box where you want to abandon a
debounced call when the component unmounts), it's a small addition:

```js
function debounce(fn, delay = 300) {
  let timeoutId;

  function debounced(...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  }

  debounced.cancel = () => clearTimeout(timeoutId);
  return debounced;
}
```

That's the whole upgrade path: start simple, add exactly the behavior you
need when you need it, and skip the dependency until the hand-rolled
version actually starts to hurt.
