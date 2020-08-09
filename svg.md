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
