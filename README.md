# Hackintosh

Some information and kext files for my dual boot hackintosh configuration running on Mac OS X El Capitan (10.11.6) and Windows 10 Pro.

## Hardware
- Asus MAXIMUS VIII HERO

- Intel® Core™ i5-4670K

- Galax Geforce GTX 980

- Samsung 840 PRO 256GB SSD

## Set up

- Create a [bootable](https://eladnava.com/install-os-x-10-11-el-capitan-on-hackintosh-vanilla/) El Capitan USB with clover installed.

- Use hashwell `config.plist` from [rampagedev](http://www.rampagedev.com/?page_id=144).

- Disable SIP via `RtVriables`
    - BooterConfig = 0x28

    - CsrActiveConfig = 0x3

- Boot with `nv_disable=1`.

- [Fix USB](http://www.insanelymac.com/forum/topic/308325-guide-1011-full-speed-usb-series-89-keeping-vanilla-sle/page-9#entry2175618) with Clover kext patch.

- Copy `FakeSMC.kext` and `IntelMausiEthernet.kext` to `EFI/CLOVER/kexts/10.11`.


## El Capitan

- Install El Capitan from the USB drive.

- Use `OsxAptioFix2Drv` instead to fix memory errors.

- Find a new `FakeSMC.kext` to fix `Service exited with abnormal code: 255` if error occurs.

- Make sure the `EFI/CLOVER/kexts` folder is loaded.

- Once El Capitan is installed, install Clover on El Capitan drive.

- Install Nvidia web drivers.

- Remove boot flag `nv_disable=1` from `config.plist` and use `nvda_drv=1` to enable GPU.

- NOTE: Use a native USB port ! Important

## Windows 10

- Create a bootable UEFI Windows 10 USB. (Rufus on Windows or UNetbootin on Mac)

- Set up El Capitan drive with a new partition.

- Format it as HFS+ Journaled.

- Install Windows 10 via USB.

- After installation, boot back into El Capitan via El Capitan USB because Windows bootloader overwrites everything. [Source](http://www.macbreaker.com/2016/04/dual-boot-windows-os-x-same-hard-disk-clover.html)

- Rename `EFI/Microsoft/Boot/bootmgfw.efi` to something else and reinstall Clover so that we can use Clover as the EFI bootloader.

- Now dual booting Windows 10 and El Capitan should work.

## Clover Bootloader

- Use custom entries in Clover to get a beautiful bootloader.

- To use custom entires, the UUID of the hard drives is needed.

- To get the UUID, press spacebar on the hard drives in clover bootloader.

- [Source](https://www.youtube.com/watch?v=waJeLVZwXUA)

## Misc.

Still deciding the audio drivers.
