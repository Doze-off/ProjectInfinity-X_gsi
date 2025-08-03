<div align="center">
  <a href="https://github.com/ProjectInfinity-X">
    <img src="https://raw.githubusercontent.com/ProjectInfinity-X/.github/main/profile/Infinity.png" width="70%" />
  </a>
</div>


Infinity X GSI
------------------


Getting Started
---------------


You'll need to get familiar with [Git and Repo](https://source.android.com/source/using-repo.html) as well as [How to build a GSI](https://github.com/phhusson/treble_experimentations/wiki/How-to-build-a-GSI%3F).



Building the GSI
---------------

**Create the directory**
```bash
mkdir infinity
cd infinity
```

**To initialize your local repository using the Infinity source, use a command like this:**

```bash
repo init --depth=1 --no-repo-verify --git-lfs -u https://github.com/ProjectInfinity-X/manifest -b 15 -g default,-mips,-darwin,-notdefault
```
**Sync up with this command:**
```bash
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j48
```

---------------
**clone all repo** 

```bash
git clone https://github.com/TrebleDroid/vendor_interfaces -b android-15.0 vendor/interfaces

git clone https://github.com/TrebleDroid/device_phh_treble -b android-15.0 device/phh/treble

git clone https://github.com/TrebleDroid/treble_app -b master treble_app

git clone https://github.com/AndyCGYan/android_packages_apps_QcRilAm -b master packages/apps/QcRilAm

git clone https://github.com/TrebleDroid/vendor_hardware_overlay -b pie vendor/hardware_overlay

git clone https://android.googlesource.com/platform/prebuilts/vndk/v28  prebuilts/vndk/v28

git clone https://android.googlesource.com/platform/prebuilts/vndk/v29 prebuilts/vndk/v29

git clone https://github.com/ponces/treble_adapter -b master treble_adapter

git clone https://github.com/Doze-off/patches.git -b patches-15 patches
```

---------------
Move the **apply-patches.sh** script inside the patches folder to the **main folder**

**Use the command:**
```bash
bash apply-patches.sh ~/infinity
```
**Note:** if some patches fail, you have to apply them manually


---------------
Move the files **AndroidProducts.mk, infinity.mk, infinity_gsi.mk** to folder, **device/phh/treble**

**Compilation: Follow the commands**
```bash
source build/envsetup.sh
lunch infinity_gsi-userdebug
m systemimage -j48
```
**Compress:**
```bash
xz -9 -T0 -v -z out/target/product/tdgsi_arm64_ab/system.img
```
