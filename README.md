<div align="center">
  <a href="https://github.com/ProjectInfinity-X">
    <img src="https://raw.githubusercontent.com/ProjectInfinity-X/.github/main/profile/Infinity.png" width="70%" />
  </a>
</div>


Infinity X GSI
------------------

This is a GSI trebledroid with patches for specific devices, BPF bypass, firewall bypass, and much more.

------------------

Create an overlay for your device to increase compatibility with GSI.

build_overlay:

Manual method: 
For creating an overlay, follow this guide: How to create an overlay https://github.com/TrebleDroid/treble_experimentations/wiki/How-to-create-an-overlay%3F?
Before submitting your overlay to the repository, make a correction using the #fix_overlay note in support group.

Semi-automatic tool: 
Required Linux pc or Termux, automatically creates flashable module: https://github.com/uzbforce/treble-rro-creator

Submit your overlay to this repository: https://github.com/Doze-off/vendor_hardware_overlay

---

Verify Overlay Status

PC:
adb shell cmd overlay list --user current

Termux:
su
cmd overlay list --user current

You should see something like:
android
[x]
me.phh.treble.overlay.hotwav.w10pro

------------------

How to flash ?

🚨Test first in dsu sideloader use [DSU Sideloader](https://github.com/VegaBobo/DSU-Sideloader)

There is no universal installation method, as each device has some different commands, but the one that works best is this one 

You can get vbmeta from the stock rom or from google

🟢 Clean Flash (GSI):

fastboot devices 

fastboot --disable-verification flash vbmeta vbmeta.img 

fastboot --disable-verity --disable-verification flash vbmeta_system vbmeta_system.img 

fastboot reboot fastboot 

fastboot erase system 

fastboot flash system system.img 

fastboot reboot recovery 
→ Clear data/cache
→ Factory reset

⚠️ Error: "out of space" when flashing, use: 
fastboot delete-logical-partition product 

❗️If the error persists, use:
fastboot delete-logical-partition system 
fastboot create-logical-partition system 0 

🔴 Dirty Flash: 
fastboot flash system system.img

------------------

### Support Group: [DozeOff GSI Treble](https://t.me/dozeoff_treble)

Big thanks for @TrebleDroid for some patches
