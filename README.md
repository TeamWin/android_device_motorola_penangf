### TWRP device tree for moto g23/13 (penangf)

=========================================

The moto g23 (codenamed _"penangf"_) is a mid-range smartphone from Motorola.

It was released in January 2023.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core CPU with 6x Arm Cortex-A55 up to 1.8GHz and 2x Arm Cortex-A75 up to 2.0GHz
Chipset | Mediatek Helio G85
GPU     | Mali-G52 MC2
Memory  | 8/4 GB RAM
Shipped Android Version | 13
Storage | 128/64 GB (eMMC 5.1)
Battery | Li-Po 5000 mAh, non-removable
Display | 720 x 1600 pixels, 6.5 inches, 60/90 hz

## Features

Works:

- [X] ADB
- [X] Decryption
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [ ] Vibrator

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/motorola/penangf" name="penangf/android_device_motorola_penangf-twrp" remote="github" revision="android-12.1" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
breakfast penangf
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot out/target/product/penangf/vendor_boot.img
```
