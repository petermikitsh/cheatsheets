# VirtualBox

## Increase Graphics memory beyond GUI max of 128 MB (to 256 MB)

```
vboxmanage modifyvm "nameOfVM" --vram 256
```

## Set scale factor to 2x (for Retina displays)

```
VBoxManage setextradata "nameOfVM" GUI/ScaleFactor 2
```
