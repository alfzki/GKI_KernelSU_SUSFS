### This is a repository for automatically building GKI kernels

> For non-GKI users, you can try the resources at [SukiSU Cloud Drive](https://alist.shirkneko.top). These are not supported on OnePlus ColorOS 14 and 15.

> First-time users must **read the following carefully** to avoid wasting other people's time!

>> Recent updates: 1. OnePlus 8 ELITE processor can use kernel 6.6 (untested); 2. Fixed compilation errors for these GKI versions—[5.10.(66, 81, 101), 5.15.(74, 94, 104)]

### Download You can download your resources [here](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases)

1. Regarding Anykernel3.zip, download and use immediately! - Then use flashing software, such as [HorizonKernelFlasher](https://github.com/libxzr/HorizonKernelFlasher/releases), to flash the kernel.

2. Regarding boot.img, download one that matches your kernel format (uncompressed, gz, lz4). [Refer to](https://kernelsu.org/zh_CN/guide/installation.html#install-by-kernelsu-boot-image) in the section on **Finding a Suitable boot.img**

- Use [FASTBOOT](https://magiskcn.com/) to flash, or use flashing software to flash it to the boot partition of the ROOT slot (e.g., iPlay, Kernelflasher).

### Support

| Features | Description |

| --- | --- |

| [KernelSU](https://kernelsu.org/zh_CN/) | Includes **original, MKSU, SUKISU, NEXT** |

| [SUSFS4](https://gitlab.com/simonpunk/susfs4ksu) | A kernel-level patch to assist with KSU's hidden features |

[BBR](https://blog.thinkin.top/archives/ke-pu-bbrdao-di-shi-shi-me) | TCP congestion control algorithm for faster networks? | | [Wireguard](https://zh.wikipedia.org/wiki/WireGuard) | Refer to the wiki link on the left |

| [LZ4KD](https://github.com/ShirkNeko/SukiSU_patch/tree/main/other) | Reportedly from the ZRAM algorithm in the HUAWEI source, patched by [云之枫](http://www.coolapk.com/u/24963680) |

<details>

<summary>Also supports these algorithms, which can be switched in the scene's ZRAM</summary>

### LZ4K, LZ4HC, deflate, 842, ~~zstdn~~, lz4k_oplus

</details>

### KSU Manager After compilation, you will see a file similar to `Next-Manager(12600)`, which is simply the latest manager uploaded along with the kernel.

![Example](./assets/get_manager.gif) Similarly, the [Release](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases) also includes the latest manager!

![release](./assets/release_manager.gif)

### Emergency Rescue Guide

> [!IMPORTANT]

> **Triggering Conditions**

> Rescue is required when the device fails to boot for the following reasons:

> - Flashing an incorrect/incompatible kernel

> - Kernel version incompatibility (e.g., flashing kernel version 233 on 5.10.66)

1. Enter FASTBOOT mode

- Physical key combination: Power + Volume Down or ADB command: `adb reboot bootloader`

2. Execute the flashing command

```bash

$ fastboot flash boot <full name of boot.img file>

```
### Source Image Acquisition Methods

1. Extract from existing firmware

- Flashable package: After decompression, use the [payload-dumper tool](https://magiskcn.com/payload-dumper-go-boot.html)

- 1. Flashable Package: Directly extract boot.img

2. External Resource Acquisition

- Community Platform Search: Device Model + Original Boot (e.g., XDA/Coolapk)

- [Mobile Online Extraction Remote Acquisition](https://magiskcn.com/payload-dumper-compose.html)

> [!TIP]

> ### Kernel Version Compatibility Notes

>
> **1. Cross-Subversion Flashing Rules**

> When the phone's GKI main version is 5.10.x (e.g., 5.10.168), it can flash a higher subversion kernel (e.g., 5.10.198) within the same main version.

Regarding the **X-lts** version, taking `android12-5.10.X-lts-AnyKernel3.zip` as an example:

**X-lts** indicates Long Term Support (LTS) (the largest sub-version number, currently 5.10.236 in this example)

**LTS** will continuously increment its build version number as the GKI source code is updated (other versions like 198 are permanently fixed).

**⚠️ Note:** While LTS is the latest version, **the latest version ≠ the most stable (e.g., 6.6.x has an automatic reboot bug)**

**2. Kernel Version Disguise Method**

Execute the following in the MT Manager terminal:

``bash

`uname -r | sed 's/^[^-]*//'

```

After obtaining the version number, simply copy it and enter it into the Action build panel to disguise the kernel version. >

**3. Compilation Optimization Suggestions**


Modify the configuration file (.github/workflows/kernel-a12-5.10.yml) (e.g., kernel-a12-5.10.yml):


- ▶️ Delete/comment out unnecessary GKI version configurations (**speed up compilation**)


- ➕ Add a specified GKI version (refer to the [Customization Guide](https://www.coolapk.com/feed/62820671?shareKey=OGMxYmZmNTk0YzIxNjgxNzM1MzI~&shareUid=11253396&shareFrom=com.coolapk.market_15.2.2))


- 📅 Kernel build time, refer to the comment around line 490 in the [gki-kernel.yml](.github/workflows/gki-kernel.yml) file. Make revisions

### More details

Feel free to leave your comments...I'll try!