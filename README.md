# android_device_xiaomi_sagit
Tree for building TWRP for Xiaomi MI 6

## Note
Only compatible with Android 11 and newer

## To compile

repo init --depth=1 -b twrp-12.1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git

. build/envsetup.sh && lunch twrp_sagit-eng

mka adbd recoveryimage

### Special Notes for this branch
- Device makefile in the device tree and dependencies file should use the "twrp" prefix.
- Currently, decryption on 12.1 is a work in progress (WIP). Decryption is only fully functional (i.e. works with password/PIN/pattern) on legacy Pixel devices that use weaver but do not use wrappedkey. On other devices, decryption will only work if no password/PIN/pattern is set in Android.
- FDE decryption is not presently supported in this branch.
- In order to successfully build in this branch, the following patch(es) will need to be cherry-picked:

    - [fscrypt: wip](https://gerrit.twrp.me/c/android_bootable_recovery/+/5405)
    - [fscrypt: move functionality to libvold](https://gerrit.twrp.me/c/android_system_vold/+/5540)

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core (4x2.45 GHz Kryo & 4x1.9 GHz Kryo)
Chipset | Qualcomm MSM8998 Snapdragon 835
GPU     | Adreno 540
Memory  | 6 GB RAM
Shipped Android Version | 7.1.1
Storage | 64/128 GB
Battery | Li-Po 3350 mAh battery
Display | 1080 x 1920 pixels, 5.15 inches (~428 ppi pixel density)
Rear Camera  | Dual 12 MP (27mm, f/1.8, OIS 4-axis & 52mm, f/2.6), phase detection autofocus, dual-LED (dual tone) flash


## Device picture

![Xiaomi Mi 6](https://xiaomi-mi.com/uploads/CatalogueImage/xiaomi-mi-6-exclusive-edition-6gb128gb-dual-sim-ceramic-black-01_15554_1492602917.jpg "Xiaomi Mi 6 in black")

## Kernel Source

https://github.com/Miccia94/kernel_xiaomi_msm8998/tree/twrp
