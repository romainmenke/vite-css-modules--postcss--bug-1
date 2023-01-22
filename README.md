CSS Modules plugins for PostCSS run at the very end of processing your CSS.
Combined with `composes` this can cause issues.

Any CSS from `bar.module.css` won't be processed by your preferred PostCSS plugins :

```css
.foo {
  color: color(display-p3 0 0 1);
  composes: bar from './bar.module.css';
}
```

Use [`postcss-import`](https://github.com/postcss/postcss-import) to fix the issue :


```css
@import url(./bar.module.css);

.foo {
  color: color(display-p3 0 0 1);
  composes: bar;
}
```
