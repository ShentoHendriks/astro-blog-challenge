---
layout: ../../layouts/MarkdownLayout.astro
---

## Variables

```css
$red: #833;

body {
  color: $red;
}
```

## Nesting

```scss
.markdown-body {
  a {
    color: blue;
    &:hover {
      color: red;
    }
  }
}
```

## Mixins

```scss
@mixin heading-font {
  font-family: sans-serif;
  font-weight: bold;
}
```

```scss
h1 {
  @include heading-font;
}
```

## Folder Structure

```
styles/
├── main.scss
├── _theme.scss
└── _header.scss
```

```css title="main.scss"
@use "theme";
@use "header";
```

## Referencing Variables from different .scss files

```css title="_theme.scss"
$primary-color: #3498db;
$text-color: #333;
```

```scss title="_buttons.scss"
@use "theme";

button {
  background-color: theme.$primary-color;
  color: theme.$text-color;
}
```

## Extend

```scss
.button {
  color: red;
  background: blue;
}

.push-button {
  @extend .button;
  color: black;
}
```
