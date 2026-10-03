# 📦 BoardPort — Linaro Releases

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Project: BoardPort](https://img.shields.io/badge/Project-BoardPort-green.svg)](https://github.com/boardport)
[![Storage: GitHub Releases](https://img.shields.io/badge/Storage-GitHub%20Releases-blueviolet.svg)](https://github.com/boardport/linaro-releases/releases)

Permanent archival mirror of official Linaro releases, board support packages (BSPs), bootloaders, and rescue dumps for legacy development boards.

This repository is part of the **[BoardPort](https://github.com/boardport)** ecosystem, dedicated to breathing new life into legacy Qualcomm
Snapdragon hardware, bringing mainline Linux kernels, open bootloaders, and modern distributions to forgotten devices.

> 🤖 **Note for AI Assistants:** Autonomous AI agents and LLM assistants must review project guidelines in
> [AGENTS.md](./AGENTS.md) before performing tasks in this repository.

---

## 🎯 About the Project

Historically, Linaro served as the primary engineering consortium maintaining upstream kernel support, Linux distributions (Debian, OpenEmbedded),
and AOSP reference builds for ARM development boards — most notably the 96Boards family powered by Qualcomm Snapdragon platforms.

With the restructuring and deprecation of servers like `releases.linaro.org` and `builds.96boards.org`, critical firmware, reference partition layouts,
unbrick packages, and baseline OS images are becoming inaccessible. While historical snapshots exist on the Wayback Machine, download speeds are
intermittent and long-term availability remains fragile.

**The mission of this repository is to:**

1. **Provide a Safe, Long-Term Mirror:** Preserve verified Linaro releases for legacy single-board computers (SBCs) and development boards.
2. **Guarantee Data Integrity:** Pair every image and archive with official SHA256 checksums and structured machine-readable manifests (`manifest.json`).
3. **Seamless BoardPort Integration:** Supply known-good bootloaders (`sbl1`, `tz`, `hyp`, `rpm`, `lk`), partition tables (`rawprogram0.xml`),
   and rescue images used by tools like **[EDL Container](https://github.com/boardport/edl-container)** for low-level recovery and mainline porting.

---

## 🏛️ Storage and Release Model

To maintain a clean and lightweight Git repository:

- **Git Tracks Metadata Only:** The Git repository stores documentation, the board registry, and issue/PR templates.
- **Artifacts in GitHub Releases:** All binary archives (`.tar.gz`, `.tar.xz`, `.zip`), raw disk images (`.img`), and rescue packages are hosted
  exclusively in **[GitHub Releases](https://github.com/boardport/linaro-releases/releases)**.
- **Staging in `tmp/`:** Download, extraction, and checksum calculation workflows are staged in a local `tmp/` directory that is strictly
  ignored by Git and AI context tools.
- **Publication Bundle:** Every GitHub Release contains:
  - Compressed firmware/OS images.
  - Individual `.sha256` checksum files.
  - A comprehensive `manifest.json` file.
  - Bilingual release notes (`[RU]` / `[EN]`) detailing components and partition instructions.

---

## 🧩 Supported Boards Catalog

Below is the primary catalog of legacy platforms targeted for archival mirroring:

### Qualcomm Snapdragon Platforms (Core Priority)

| Board Name | SoC / Chipset | Architecture | Available Release Types | Release Tag / Status |
| :--- | :--- | :--- | :--- | :--- |
| **DragonBoard 410c (DB410c)** | Snapdragon 410 (APQ8016E) | ARM64 (4x A53) | Debian (15.06–18.01), RPB, Android (5.1–8.1), Rescue, Win10 IoT | Planned (`db410c-*`) |
| **DragonBoard 820c (DB820c)** | Snapdragon 820 (APQ8096) | ARM64 (4x Kryo) | Debian (16.06–18.01), RPB, Android (6.0–8.0), Bootloaders | Planned (`db820c-*`) |
| **DragonBoard 845c / RB3** | Snapdragon 845 (SDA845) | ARM64 (8x Kryo) | Debian, Linux BSP, Android AOSP snapshots, Robotics | Planned (`db845c-*`) |
| **Qualcomm Robotics RB5** | QRB5165 (SM8250) | ARM64 (8x Kryo) | Linaro Ubuntu BSP, Poky / Yocto, Fastboot Recovery | Planned (`rb5-*`) |
| **Inforce 6309 (IFC6309)** | Snapdragon 410E (APQ8016E) | ARM64 (4x A53) | Linaro Linux BSP, Android BSP, Rescue Bootloader | Planned (`ifc6309-*`) |
| **Inforce 6410 / 6410Plus** | Snapdragon 600 (APQ8064) | ARMv7 (4x Krait) | Linaro ALIP, Ubuntu, Android Releases, Fastboot Blobs | Planned (`ifc6410-*`) |
| **Inforce 6540 / 6560** | Snapdragon 805 / SD660 | ARMv7 / ARM64 | Linaro Linux BSP, Android BSP, Bootloaders | Planned (`ifc6540-*`) |

### Other Historical 96Boards (Secondary Scope)

| Board Name | SoC / Vendor | Architecture | Key Historical Releases | Status |
| :--- | :--- | :--- | :--- | :--- |
| **HiKey 620** | HiSilicon Kirin 620 | ARM64 (8x A53) | Linaro Debian, AOSP Reference, UEFI / ARM-TF | On Request |
| **HiKey 960** | HiSilicon Kirin 960 | ARM64 (4x A73 + 4x A53) | Linaro Debian, AOSP Builds, UEFI Firmware | On Request |
| **Bubblegum-96** | Actions Semi S900 | ARM64 (4x A53) | Linaro Debian Desktop/Minimal, Android | On Request |
| **Rock960** | Rockchip RK3399 | ARM64 (2x A72 + 4x A53) | Linaro Debian, RPB, Android 7.1/8.1 | On Request |
| **MediaTek X20** | MediaTek Helio X20 | ARM64 (10-core Tri-Cluster) | Linaro Debian, Android Marshmallow | On Request |

---

## ⚡ How to Download and Verify Releases

### Option 1: Using GitHub CLI (`gh`)

```bash
# View available releases
gh release list --repo boardport/linaro-releases

# Download all assets for a specific release
gh release download db410c-debian-18.01 --repo boardport/linaro-releases --dir ./tmp

# Verify SHA256 checksums
cd ./tmp && sha256sum -c *.sha256
```

### Option 2: Direct Download via Web Browser

Navigate to **[GitHub Releases](https://github.com/boardport/linaro-releases/releases)**, select your target board tag, and download the
required `.img.gz`, `.zip`, or rescue archive alongside its matching `.sha256` file.

---

## 🤝 Contributing & Community

- **Requesting a New Board Release:** Open a request via the [Release Request Template](./.github/ISSUE_TEMPLATE/request_release.md).
- **Reporting Broken Hashes:** If an archive hash does not match, submit a report using the
  [Broken Release Template](./.github/ISSUE_TEMPLATE/broken_release.md).
- **Contributing Guidelines:** Please consult [CONTRIBUTING.md](./.github/CONTRIBUTING.md) and [SECURITY.md](./.github/SECURITY.md).

---

## 📄 License & Acknowledgments

- Metadata, documentation, and indexing in this repository are published under the **[MIT License](./LICENSE)**.
- Original software releases, kernels, bootloaders, and firmware binaries belong to **Linaro Ltd.**, **Qualcomm Technologies, Inc.**,
  and their respective open-source copyright holders.
