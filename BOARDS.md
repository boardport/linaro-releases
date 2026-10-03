# 📋 BoardPort — Hardware Platforms & Releases Catalog

This document provides a comprehensive technical registry of development boards, single-board computers (SBCs),
and robotics kits supported by the **[BoardPort](https://github.com/boardport)** Linaro releases mirror.

Here you will find hardware specifications, official and historical upstream resources, release preservation matrices,
boot mode configurations, and call-for-preservation guidelines for missing assets.

---

## 📌 Release Status Legend

| Status | Meaning |
| :---: | :--- |
| ✅ **Mirrored** | 100% complete — verified and published in [GitHub Releases](https://github.com/boardport/linaro-releases/releases). |
| ⚠️ **Partial** | Bootchain & kernel complete — rootfs image missing from upstream web archives. |
| 🔍 **Wanted** | Preserved build missing in web archives; community submissions requested. |
| 🔄 **Compatible** | Hardware compatible with an existing mirrored board release suite. |

---

## 🧩 Qualcomm Snapdragon Platforms (Core Priority)

### 1. DragonBoard 410c (DB410c)

- **Processor (SoC):** Qualcomm Snapdragon 410 (APQ8016E)
- **CPU:** Quad-core ARM Cortex-A53 up to 1.2 GHz (ARMv8-A 64-bit)
- **GPU:** Qualcomm Adreno 306 @ 400 MHz
- **DSP:** Qualcomm Hexagon QDSP6 v5
- **Memory & Storage:** 1 GB / 2 GB LPDDR3 @ 533 MHz, 8 GB eMMC 4.51, MicroSD card slot
- **Standard:** 96Boards Consumer Edition (CE)

#### Official & Upstream Links

- **96Boards Product Page:** [96boards.org/product/dragonboard410c](https://www.96boards.org/product/dragonboard410c/) *(Archived / EOL)*
- **Arrow Electronics Page:** [arrow.com/.../dragonboard410c](https://www.arrow.com/en/products/dragonboard410c/) *(Discontinued)*
- **Qualcomm Developer Network:** [developer.qualcomm.com/hardware/dragonboard-410c](https://developer.qualcomm.com/hardware/dragonboard-410c) *(Legacy)*
- **Linaro Documentation:** [Linaro DB410c Wiki](https://web.archive.org/web/20200806085521/https://wiki.linaro.org/Boards/DragonBoard410c)
  *(Wayback Machine)*

> [!NOTE]
> **Support Status:** Officially End-of-Life (EOL). All official downloads on Linaro and Qualcomm servers are discontinued.

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Rescue 21.12** | Build 176 | SBL1, TrustZone, Hyp, RPM, LK Fastboot, Firehose EDL 9008 | [`db410c-rescue-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-21.12) | ✅ Mirrored |
| **Linaro Debian 21.12** | Build 1125 | Kernel 5.15.0 LTS, DTB, initramfs, Fastboot boot & installer images | [`db410c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-21.12) | ⚠️ Partial* |
| **Qualcomm BSP Firmware** | r1036.1 (Latest) | Adreno 306 GPU, Venus, WCN3660 Wi-Fi/BT blobs | [`db410c-firmware-r1036`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1036) | ✅ Mirrored |
| **Qualcomm BSP Firmware** | r1034.2.1 | Adreno 306, DSP, WCN3660 blobs | [`db410c-firmware-r1034`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1034) | ✅ Mirrored |
| **Qualcomm BSP Firmware** | r1032.1 | Adreno 306, DSP, WCN3660 blobs | [`db410c-firmware-r1032`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1032) | ✅ Mirrored |
| **Linaro Rescue 17.09** | Build 88 | Linux & Android eMMC bootloader suites, EDL 9008 | [`db410c-rescue-17.09`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-17.09) | ✅ Mirrored |
| **Qualcomm Boot Tools** | 2024.05 | Partition layout compiler (`ptool.py`), SD rescue generator (`mksdcard`) | [`db410c-boot-tools`](https://github.com/boardport/linaro-releases/releases/tag/db410c-boot-tools) | ✅ Mirrored |
| **Linaro Debian 16.06** | Build 110 | Kernel 4.4.9, DTB, `dt.img`, initramfs, `.config` | [`db410c-debian-16.06`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-16.06) | ⚠️ Partial* |
| **Qualcomm Android BSP** | 16.03 | LK Fastboot, Android 5.1.1 ramdisks, device tree, pinned repo manifest | [`db410c-android-16.03`](https://github.com/boardport/linaro-releases/releases/tag/db410c-android-16.03) | ⚠️ Partial* |

*\* Note: Boot chain is 100% complete. Large upstream rootfs images are missing in web archives. See [Community Preservation Call](#-community-preservation-call).*

#### Hardware Boot Switch Configuration (S6)

The DragonBoard 410c features a 4-position DIP switch (**S6**) on the bottom:

| Switch | Function | Position: OFF (Default) | Position: ON |
| :---: | :--- | :--- | :--- |
| **1** | USB Host / Device | USB Host (Type-A active) | USB Device (Micro-USB OTG active) |
| **2** | Boot Device | Boot from internal eMMC | **Boot from MicroSD card (SD Rescue)** |
| **3** | Boot Mode Select | Normal boot | Fastboot mode on boot |
| **4** | Reserved | Normal operation | Force EDL (Qualcomm 9008 download mode) |

---

### 2. DragonBoard 820c (DB820c)

- **Processor (SoC):** Qualcomm Snapdragon 820 (APQ8096)
- **CPU:** Quad-core Qualcomm Kryo 64-bit (2x 2.15 GHz + 2x 1.6 GHz)
- **GPU:** Qualcomm Adreno 530 @ 624 MHz
- **DSP:** Qualcomm Hexagon 680 DSP (with Hexagon Vector eXtensions)
- **Memory & Storage:** 3 GB LPDDR4 @ 1866 MHz, 32 GB UFS 2.0 gear 3, MicroSD card slot
- **Standard:** 96Boards Consumer Edition (CE)

#### Official & Upstream Links

- **96Boards Product Page:** [96boards.org/product/dragonboard820c](https://www.96boards.org/product/dragonboard820c/) *(Archived)*
- **Arrow Electronics Page:** [arrow.com/.../dragonboard820c](https://www.arrow.com/en/products/dragonboard820c/) *(Discontinued)*
- **Linaro Releases (Original):** `releases.linaro.org/96boards/dragonboard820c/` *(Server offline)*
- **Validation Mirror:** `images.validation.linaro.org/snapshots.linaro.org/96boards/dragonboard820c/`

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian 21.12** | Build 869 | Linux kernel 5.15.0 LTS, DTB, initramfs, Fastboot boot image | [`db820c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db820c-debian-21.12) | ⚠️ Partial* |
| **Rescue & UFS Bootloader** | Build 83636 | XBL, TrustZone, Hyp, Little Kernel, Firehose 9008, GPT LUN 0–5 | [`db820c-rescue-83636`](https://github.com/boardport/linaro-releases/releases/tag/db820c-rescue-83636) | ✅ Mirrored |
| **Qualcomm BSP Firmware** | r01700.1 | Adreno 530 GPU, Venus decoder, Hexagon DSP, WLAN calibration | [`db820c-firmware-r01700`](https://github.com/boardport/linaro-releases/releases/tag/db820c-firmware-r01700) | ✅ Mirrored |

#### Boot Modes

- **Fastboot Mode:** Hold button **S4 (Vol-)** while connecting 12V DC power.
- **Emergency EDL Recovery (9008):** Use `prog_ufs_firehose_8996_ddr.elf` from release `db820c-rescue-83636`.

---

### 3. DragonBoard 845c / Qualcomm Robotics RB3

- **Processor (SoC):** Qualcomm Snapdragon 845 (SDA845)
- **CPU:** Octa-core Qualcomm Kryo 385 (4x 2.8 GHz Gold + 4x 1.8 GHz Silver)
- **GPU:** Qualcomm Adreno 630 @ 710 MHz
- **DSP:** Qualcomm Hexagon 685 DSP with HVX
- **Memory & Storage:** 4 GB LPDDR4x, 64 GB UFS 2.1, MicroSD card slot
- **Standard:** 96Boards Consumer Edition (CE)

#### Official & Upstream Links

- **96Boards Product Page:** [96boards.org/product/rb3-platform](https://www.96boards.org/product/rb3-platform/) *(Archived)*
- **Thundercomm RB3 Page:** [thundercomm.com/.../qualcomm-robotics-rb3](https://www.thundercomm.com/product/qualcomm-robotics-rb3-platform/)
- **Linaro Validation Mirror:** `images.validation.linaro.org/.../dragonboard845c/`

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Qualcomm BSP Firmware** | v4 | Adreno 630 GPU, Hexagon 685 DSP, Venus, WCN3990 Wi-Fi/BT | [`db845c-firmware-v4`](https://github.com/boardport/linaro-releases/releases/tag/db845c-firmware-v4) | ✅ Mirrored |
| **Rescue & UFS Bootloader** | Build 101 | XBL, TrustZone, Hyp, QUPv3, Firehose EDL 9008, GPT LUN 0–5 | [`db845c-rescue-101`](https://github.com/boardport/linaro-releases/releases/tag/db845c-rescue-101) | ✅ Mirrored |
| **Linux RPB Console** | Build 169 | Kernel 5.1 Fastboot boot image + OpenEmbedded rootfs (145 MB) | [`db845c-linux-rpb-169`](https://github.com/boardport/linaro-releases/releases/tag/db845c-linux-rpb-169) | ✅ Mirrored |

#### Boot Modes

- **Fastboot Mode:** Hold button **S4 (Vol-)** while connecting 12V DC power.
- **EDL 9008 Recovery:** Use `prog_firehose_ddr.elf` from `db845c-rescue-101`.

---

### 4. Qualcomm Robotics RB5 (QRB5165)

- **Processor (SoC):** Qualcomm QRB5165 / SM8250
- **CPU:** Octa-core Qualcomm Kryo 585 (1x 2.84 GHz Prime + 3x 2.42 GHz Gold + 4x 1.8 GHz Silver)
- **GPU:** Qualcomm Adreno 650
- **DSP:** Qualcomm Hexagon 698 DSP with dual HVX & NPU
- **Memory & Storage:** 8 GB LPDDR5, 128 GB UFS 3.0, MicroSD card slot

#### Official & Upstream Links

- **96Boards Product Page:** [96boards.org/product/rb5-platform](https://www.96boards.org/product/rb5-platform/)
- **Thundercomm RB5 Page:** [thundercomm.com/.../qualcomm-robotics-rb5](https://www.thundercomm.com/product/qualcomm-robotics-rb5-development-kit/)
- **Linaro Validation Mirror:** `images.validation.linaro.org/.../qrb5165-rb5/`

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Rescue & UFS Bootloader** | Build 27 | XBL, TrustZone, Hyp, ABL Fastboot, Firehose 9008, GPT LUN 0–5 | [`rb5-rescue-27`](https://github.com/boardport/linaro-releases/releases/tag/rb5-rescue-27) | ✅ Mirrored |
| **Linaro QCOM LT Linux** | Kernel 5.13.9 (708) | Official Qualcomm Landing Team mainline kernel 5.13 boot image | [`rb5-linux-5.13`](https://github.com/boardport/linaro-releases/releases/tag/rb5-linux-5.13) | ✅ Mirrored |

#### Boot Modes

- **Fastboot Mode:** Hold **FST_BOOT / S1** button while applying 12V DC power.
- **EDL 9008 Recovery:** Use `prog_firehose_ddr.elf` from release `rb5-rescue-27`.

---

### 5. Qualcomm Robotics RB2 (QRB4210)

- **Processor (SoC):** Qualcomm QRB4210 / Qualcomm Dragonwing
- **CPU:** Octa-core Qualcomm Kryo 260
- **GPU:** Qualcomm Adreno 610
- **Memory & Storage:** 4 GB LPDDR4x, 64 GB eMMC 5.1

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian Bookworm** | Build 58915 | Fastboot boot image with kernel, QRB4210 DTB, and Bookworm initrd | [`rb2-debian-bookworm`](https://github.com/boardport/linaro-releases/releases/tag/rb2-debian-bookworm) | ✅ Mirrored |

---

### 6. Inforce IFC6410 / IFC6410Plus

- **Processor (SoC):** Qualcomm Snapdragon 600 (APQ8064 / APQ8064-1AA)
- **CPU:** Quad-core Qualcomm Krait 300 up to 1.7 GHz (ARMv7-A 32-bit)
- **GPU:** Qualcomm Adreno 320 @ 400 MHz
- **DSP:** Qualcomm Hexagon QDSP6 v4
- **Memory & Storage:** 2 GB DDR3, 4 GB eMMC, SATA 3Gbps port, MicroSD slot

#### Official & Upstream Links

- **Penguin Edge / Inforce:** [IFC6410 Plus SBC](https://www.penguinsolutions.com/edge-computing/products/single-board-computers/ifc6410-plus/)
  *(Legacy)*
- **Linaro Releases Archive:** `releases.linaro.org/debian/boards/snapdragon/16.02/` *(Server offline)*

#### Release Preservation Matrix

| Release Name | Upstream Build | Component Types | BoardPort Release | Status |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian 16.02** | Kernel 4.4 LTS | Boot images for eMMC, SATA (`sda1`), SD, DTB, modules, deb packages | [`ifc6410-debian-16.02`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-debian-16.02) | ✅ Mirrored |
| **Qualcomm BSP & eMMC Rescue** | r16.02 / eMMC | `/lib/firmware` blobs (Adreno 320, Wi-Fi, Venus) + raw eMMC partition dumps | [`ifc6410-firmware-rescue`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-firmware-rescue) | ✅ Mirrored |
| **Linux Kernel 5.15 LTS** | Headless LTS | Modern 5.15 LTS boot images (eMMC, SATA, SD), modules, Docker cgroups | [`ifc6410-linux-5.15`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-linux-5.15) | ✅ Mirrored |

---

### 7. Inforce IFC6309

- **Processor (SoC):** Qualcomm Snapdragon 410E (APQ8016E)
- **Architecture:** ARM64 (4x Cortex-A53)
- **Hardware Compatibility:** 100% pin- and bootloader-compatible with the DragonBoard 410c boot stack.
- **Recommended Releases:** Use [`db410c-rescue-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-21.12)
  and [`db410c-firmware-r1036`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1036).
- **Status:** 🔄 **Hardware Compatible**

---

### 8. Inforce IFC6540 / IFC6560

- **Processor (SoC):** Qualcomm Snapdragon 805 (APQ8084) / Snapdragon 660 (SDA660)
- **Status:** 🔍 **Wanted** — Community contributions of verified firmware dumps and Linaro builds are requested.

---

## 🏛️ Secondary Scope: Historical 96Boards

| Board Name | SoC / Vendor | Architecture | Key Releases | Status |
| :--- | :--- | :--- | :--- | :---: |
| **HiKey 620** | HiSilicon Kirin 620 | ARM64 (8x A53) | Linaro Debian, AOSP Reference, UEFI Firmware | 🔍 On Request |
| **HiKey 960** | HiSilicon Kirin 960 | ARM64 (4x A73 + 4x A53) | Linaro Debian, AOSP Builds, UEFI Firmware | 🔍 On Request |
| **Bubblegum-96** | Actions Semi S900 | ARM64 (4x A53) | Linaro Debian Desktop/Minimal, Android | 🔍 On Request |
| **Rock960** | Rockchip RK3399 | ARM64 (2x A72 + 4x A53) | Linaro Debian, RPB, Android 7.1/8.1 | 🔍 On Request |
| **MediaTek X20** | MediaTek Helio X20 | ARM64 (10-core Tri-Cluster) | Linaro Debian, Android Marshmallow | 🔍 On Request |

---

## 🤝 Community Preservation Call

### Missing Artifacts We Are Searching For

If you have historical archives from `releases.linaro.org` or `builds.96boards.org` stored on your local drives,
we would greatly appreciate your help in completing the following releases:

1. **DragonBoard 410c:**
   - `linaro-sid-alip-dragonboard-410c-1125.img.gz` (~1.4 GB)
   - `linaro-jessie-alip-qcom-snapdragon-arm64-20160630-110.img.gz` (~1.1 GB)
   - Official Qualcomm Android 16.03 `system.img` (~800 MB)
2. **DragonBoard 820c:**
   - `linaro-sid-alip-dragonboard-820c-869.img.gz` (~1.2 GB)
3. **Inforce 6540 (APQ8084):**
   - Official Linaro / Inforce BSP archives and fastboot bootloaders.

### How to Contribute

- **Open a GitHub Issue:** Submit a report via the [Release Request Template](./.github/ISSUE_TEMPLATE/request_release.md).
- **Verification:** Please provide the file name, byte size, MD5, and SHA256 checksums alongside your submission.
