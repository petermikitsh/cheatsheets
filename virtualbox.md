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
