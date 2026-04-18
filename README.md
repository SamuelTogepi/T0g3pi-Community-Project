# T0g3pi Community Project

T0g3pi is a tool for **arm64 iOS/iPadOS multibooting and tethered downgrades**. This CoolBooter-esque app aims to modernize the original codebase for better stability and usability.

## arm64 Dualbooting
Divisé installs a secondary iOS version alongside your current installation. It functions by creating two or more new APFS volumes (`SystemB` and `DataB`), then using `rsync` to populate the new volumes with a chosen root filesystem. Finally, Divisé configures the boot environment to allow the device to toggle between your primary and secondary OS.

## arm64 Tethered Downgrades
Divisé performs tethered downgrades by overwriting your primary OS with a chosen root filesystem. Unlike dualbooting, this **replaces** your current installation entirely. The device will be unable to boot into an untethered state until a signed version of iOS is restored via recovery mode/DFU.

## Booting
Because these modifications rely on the `checkm8` exploit (A7–A11 devices), all dualboots and tethered downgrades are **tethered**. To boot the secondary OS, you must use a computer or an OTG-connected device. Recommended tools include:
* **[Ramiel]** The recommended GUI-based solution.
* **[PyBoot]** A CLI-based automation script.
* **Manual patching:** For advanced users only.

## Compiling
*Requires macOS and a configured [Theos](https://github.com/theos/theos/wiki/Installation-macOS) environment.*

### Prerequisites
Install dependencies via [Homebrew](https://brew.sh):
```bash
brew install fakeroot ldid dpkg
```

### Build & Install
1. Ensure `THEOS` is set in your environment.
2. Edit `compile` to target your device's IP address.
3. Run the following command:
```bash
./compile 192.168.x.x
```
*Note: This script requires OpenSSH installed on the target device.*

## License & Credits
Licensed under the **GNU General Public License v3.0**. 

**Special Thanks:** 
Original project by [MatthewPierson](https://github.com/MatthewPierson). Additional thanks to PsychoTea, Pwn20wnd, Cryptiiic, and Nobbele for their foundational contributions to the arm64 jailbreak scene.
