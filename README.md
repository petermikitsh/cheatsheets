# cheatsheets

A personal collection of incantations for various technologies.

# AWS CLI

## Get ECR image versions for `myorg/myimage` sorted by creation date

Outputs a JSON string array. Useful for creating a Jenkins UI to pick a release version.

```
aws ecr describe-images --repository-name myorg/myimage \
  --profile=stg --region=us-west-2 \
  --query 'reverse(sort_by(imageDetails,& imagePushedAt))' | \
  jq 'map(.imageTags) | add'
```

```json
[
  "0.15.5",
  "0.15.4-canary-813d69f",
  "0.15.3",
  "0.15.2-canary-4c3dbfe",
  "0.15.2",
  "0.15.1",
  "0.15.0"
]
```

# Docker

## Delete all images for repo `myorg/myimage` before version `x.y.z`

Useful for managing disk space in CI environments.

```
VERSION=1.0.0
REPO_NAME=something.amazonaws.com/myorg/myimage
TAG_NAME=$REPO_NAME:$VERSION
OLD_IMAGES=$(docker images -a -q --filter=before="$TAG_NAME" --filter=reference="$REPO_NAME")
docker rmi $OLD_IMAGES
```

## Build a Dockerfile without a build context

Useful if you don't need a build context. Copying the entire current directory wastes time.

```
docker build -t myimage:latest - < Dockerfile
```

# Mac OS

## Always Show Scrollbars

Enabling this setting is helpful for spotting duplicate, nested scrollbars in HTML documents when `overflow: scroll;` is set (`overflow: auto` is preferred).

- Click the Apple menu at the top-left of the screen, then select System Preferences.
- Next, select the General preferences pane; it’s the very first one, up at the top.
- Under the “Show scroll bars” heading, you’ll find three options: “Automatically based on input device,” “When scrolling,” and “Always.”
- Go ahead and select that last “Always” option. You’re done!

Source: https://heresthethingblog.com/2015/03/10/mac-tip-macs-scroll-bars

# OS Commands

## Delete directories by glob pattern

Useful for clearing unused folders on `gh-pages` branches.

```
find . -type d -name "*-canary-*" -exec rm -rf {} \;
```

# SSH

## Persist key password

Prevents being promoted for key password. Saves time.

```
ssh-add -K ~/.ssh/id_rsa
```

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

# VirtualBox

## Increase Graphics memory beyond GUI max of 128 MB (to 256 MB)

```
vboxmanage modifyvm "nameOfVM" --vram 256
```

## Set scale factor to 2x (for Retina displays)

```
VBoxManage setextradata "nameOfVM" GUI/ScaleFactor 2
```

## Add additional CPUs (6)

```
VBoxManage modifyvm "nameOfVM" --cpus 6
```

## Add additional RAM (8 GB)

```
vboxmanage modifyvm "nameOfVM" --memory 8192
```

## Install Guest Additions

```
vboxmanage unattended install "nameOfVM" --install-additions --iso=/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso
```

## Enable 2d acceleration

```
VBoxManage modifyvm "nameOfVM" --accelerate2dvideo on
```

## Enable 3d acceleration

```
VBoxManage modifyvm "nameOfVM" --accelerate3d on
```
