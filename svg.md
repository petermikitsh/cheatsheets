# SVG

## Transparent mask

Useful for subtracting one vector from another.

```svg
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="100" height="100">
  <defs>
    <mask id="mask" x="0" y="0">
      <rect fill="white" width="100%" height="100%" fill-opacity="1" />
      <circle cx="50" cy="50" r="20" />
    </mask>
  </defs>
  <rect style="mask: url(#mask)" x="0" y="0" width="100%" height="100%" fill="#00f" />
</svg>
```

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MCA1MCI+PHBhdGggZD0iTTIyIDM4VjUxTDMyIDMybDE5LTE5djEyQzQ0IDI2IDQzIDEwIDM4IDAgNTIgMTUgNDkgMzkgMjIgMzh6Ii8+PC9zdmc+"/>

## Resize canvas to element

Useful for removing extraneous negative space bordering SVG content

- Open SVG in Inkscape
- Select all items in layer `⌘ A`
- Resize canvas `⌘ ⇧ R`

## Add `viewBox` attribute (if missing)

Specifying `viewBox` is helpful when manually setting height and/or width on an `<svg>` element.

- Open SVG in Inkscape
- Save As > Optimized SVG
- On "SVG Output" tab, check `Enable viewboxing`


## Animated, infinitely repeating gradient

- https://codepen.io/hujambo-dunia/pen/jaxLZw

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="50" version="1.1" viewBox="0 0 200 50">
  <defs>
    <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="0">
      <stop offset="0%" style="stop-color: red;" />
      <stop offset="14.28%" style="stop-color: orange;" />
      <stop offset="28.57%" style="stop-color: yellow;" />
      <stop offset="42.85%" style="stop-color: green;" />
      <stop offset="57.14%" style="stop-color: blue;" />
      <stop offset="71.42%" style="stop-color: indigo;" />
      <stop offset="85.71%" style="stop-color: violet;" />
      <stop offset="100%" style="stop-color: red;" />
    </linearGradient>
    <pattern id="pattern" x="0" y="0" width="300%" height="100%">
      <rect x="0" y="0" width="150%" height="100%" fill="url(#gradient)">
        <animate attributeName="x" from="0" to="150%" dur="2.5s" repeatCount="indefinite" />
      </rect>
      <rect x="-150%" y="0" width="150%" height="100%" fill="url(#gradient)">
        <animate attributeName="x" from="-150%" to="0" dur="2.5s" repeatCount="indefinite" />
      </rect>
    </pattern>
  </defs>
  <g fill="url(#pattern)">
    <rect x="0" y="0" width="200" height="50" />
  </g>
</svg>
```
