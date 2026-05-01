<div align="center">

# OnePlus Kernel SUSFS Builds (Wild Fork)

### OnePlus kernel builds with KernelSU variants, SukiSU Ultra, ReSukiSU and SUSFS

[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-green)](https://kernelsu.org/)
[![KernelSU Next](https://img.shields.io/badge/KernelSU--Next-Supported-brightgreen)](https://kernelsu-next.github.io/webpage/)
[![ReSukiSU](https://img.shields.io/badge/ReSukiSU-Supported-blue)](https://github.com/ReSukiSU/ReSukiSU)
[![SukiSU Ultra](https://img.shields.io/badge/SukiSU%20Ultra-Supported-purple)](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-orange)](https://gitlab.com/simonpunk/susfs4ksu)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-Automated%20Builds-blue)](https://github.com/Bouteillepleine/OnePlus_Kernel_SUSFS/actions)

</div>

---

## ⚠️ Disclaimer

Flashing a custom kernel always carries risk.

Please make sure to:

- 💾 Back up your important data.
- 🧠 Understand your exact device model and OS version.
- 📦 Keep a copy of your stock `boot`, `init_boot`, and/or `vendor_boot` images.
- 🔋 Keep enough battery before flashing.
- ✅ Flash only builds intended for your exact device and OS version.

I am **not responsible** for bricked devices, bootloops, broken hardware, lost data, failed OTA updates, broken root, or any other issue caused by using this kernel.

By flashing anything from this repository, **you choose to make these modifications yourself**.

<div align="center">

# 🚨 Proceed at your own risk

</div>

---

## 📌 About this fork

This repository is an unofficial fork/custom build workflow based on the WildKernels OnePlus KernelSU SUSFS ecosystem.

Repository:

```text
https://github.com/Bouteillepleine/OnePlus_Kernel_SUSFS
```

This fork focuses on automated OnePlus/Oppo/Realme kernel builds with selectable root variants and SUSFS integration.

### Main supported root variants

| Variant | Status | Upstream |
|---|---:|---|
| **KernelSU** | ✅ Supported | [tiann/KernelSU](https://github.com/tiann/KernelSU) |
| **KernelSU Next** | ✅ Supported | [KernelSU-Next/KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next) |
| **ReSukiSU** | ✅ Supported | [ReSukiSU/ReSukiSU](https://github.com/ReSukiSU/ReSukiSU) |
| **SukiSU Ultra** | ✅ Supported | [SukiSU-Ultra/SukiSU-Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra) |
| **SUSFS** | ✅ Integrated where supported | [simonpunk/susfs4ksu](https://gitlab.com/simonpunk/susfs4ksu) |

---

## ✨ Fork-specific features

This fork includes or is designed around:

- ✅ **SukiSU Ultra support**
- ✅ **ReSukiSU support**
- ✅ **KernelSU support**
- ✅ **KernelSU Next support**
- ✅ **SUSFS integration**
- ✅ **Selectable KSU variants using JSON**
- ✅ **Exact model filtering with `target_model`**
- ✅ **Android/kernel version filtering**
- ✅ **OxygenOS version filtering**
- ✅ **Optional release creation**
- ✅ **Optional clean build mode**
- ✅ **Optional custom build timestamp**
- ✅ **GitHub Actions build matrix generation**
- ✅ **Build summaries and release notes**

---

## 📱 Device compatibility

Before flashing, verify that your exact device configuration is supported.

Compatibility depends on:

- Device model
- OxygenOS / ColorOS / RealmeUI version
- Android version
- Kernel version
- Boot image layout
- Kernel source compatibility
- Whether SUSFS patches are available for that kernel branch

Check the repository configuration files:

- [`configs/`](./configs/)

If your exact model and OS combination is not listed, **do not flash blindly**.

---

## 🧩 GitHub Actions build workflow

Builds are generated using GitHub Actions.

Go to:

```text
Actions → Build and Release OnePlus Kernels → Run workflow
```

Repository Actions page:

```text
https://github.com/Bouteillepleine/OnePlus_Kernel_SUSFS/actions
```

---

## 🎯 Build target selection

### `op_model`

Selects the general group of devices/kernels to build.

Available options may include:

```text
OOS14+15+16
OOS15+16
OOS14+15
OOS16
OOS15
OOS14
android16-6.12
android15-6.6
android14-6.1
android13-5.15
android12-5.10
```

### `target_model`

Optional exact model filter.

Example:

```text
OP15
```

If left empty, the workflow builds all models matching `op_model`.

Example behavior:

| `op_model` | `target_model` | Result |
|---|---|---|
| `OOS16` | empty | Builds all OOS16 configs |
| `OOS16` | `OP15` | Builds only OP15 configs on OOS16 |
| `android16-6.12` | `OP15` | Builds OP15 only if it matches Android 16 / kernel 6.12 |
| `OOS14+15+16` | `OP13` | Builds OP13 across matching OS configs |

> `target_model` is an exact match. Use the same model name as shown in the config files.

---

## 🔐 KSU variant selection

The workflow accepts KSU options as JSON.

Default example:

```json
[{"type":"sukisu","hash":"main"}]
```

Supported `type` values:

```text
ksu
ksun
rsksu
sukisu
```

### Examples

Build with SukiSU Ultra:

```json
[{"type":"sukisu","hash":"main"}]
```

Build with ReSukiSU:

```json
[{"type":"rsksu","hash":"main"}]
```

Build with KernelSU Next:

```json
[{"type":"ksun","hash":"dev"}]
```

Build with original KernelSU:

```json
[{"type":"ksu","hash":"main"}]
```

Build multiple root variants in one workflow run:

```json
[
  {"type":"sukisu","hash":"main"},
  {"type":"rsksu","hash":"main"},
  {"type":"ksun","hash":"dev"}
]
```

> Release mode may require exactly one KSU option depending on workflow settings.

---

## 🛡️ SUSFS support

SUSFS is integrated where the selected device/kernel configuration supports it.

SUSFS upstream:

```text
https://gitlab.com/simonpunk/susfs4ksu
```

Default SUSFS branches are selected by Android/kernel version.

| Android / Kernel | Default SUSFS branch |
|---|---|
| `android12-5.10` | `gki-android12-5.10` |
| `android13-5.15` | `gki-android13-5.15` |
| `android14-6.1` | `gki-android14-6.1` |
| `android15-6.6` | `gki-android15-6.6` |
| `android16-6.12` | `gki-android16-6.12` |

The workflow can also accept a custom SUSFS branch or commit hash.

---

## 📦 Releases

Kernel ZIPs are published through GitHub Releases when release mode is enabled.

Releases:

```text
https://github.com/Bouteillepleine/OnePlus_Kernel_SUSFS/releases
```

Release notes may include:

- Built devices
- OS versions
- Kernel versions
- Root variant
- Root commit/hash
- SUSFS version/hash
- Feature flags
- Build configuration
- Asset list

---

## 📥 Installation guide

### Requirements

- Unlocked bootloader
- Compatible device and OS version
- Backup of stock `boot`, `init_boot`, and/or `vendor_boot`
- Kernel flashing tool
- Matching manager app

### Recommended flashing method

Use:

- [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)

General steps:

1. Download the correct AnyKernel3 ZIP for your exact device and OS version.
2. Back up your current boot-related partitions.
3. Flash the ZIP using Kernel Flasher.
4. Install the matching manager app.
5. Reboot.
6. Open the manager app and verify root status.

---

## 📱 Manager applications

| Variant | Manager / Releases |
|---|---|
| **KernelSU** | [tiann/KernelSU releases](https://github.com/tiann/KernelSU/releases) |
| **KernelSU Next** | [KernelSU-Next releases](https://github.com/KernelSU-Next/KernelSU-Next/releases) |
| **ReSukiSU** | [ReSukiSU releases](https://github.com/ReSukiSU/ReSukiSU/releases) |
| **SukiSU Ultra** | [SukiSU Ultra releases](https://github.com/SukiSU-Ultra/SukiSU-Ultra/releases) |
| **Community manager** | [WildKSU Manager](https://github.com/WildKernels/Wild_KSU/releases) |

### Recommended module

- [KSU SUSFS Module](https://github.com/sidex15/ksu_module_susfs/releases)

---

## 🔧 Related upstream repositories

<div align="center">

| Project | Repository |
|---|---|
| **WildKernels OnePlus** | [WildKernels/OnePlus_KernelSU_SUSFS](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS) |
| **WildKernels patches** | [WildKernels/kernel_patches](https://github.com/WildKernels/kernel_patches) |
| **KernelSU** | [tiann/KernelSU](https://github.com/tiann/KernelSU) |
| **KernelSU Next** | [KernelSU-Next/KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next) |
| **ReSukiSU** | [ReSukiSU/ReSukiSU](https://github.com/ReSukiSU/ReSukiSU) |
| **SukiSU Ultra** | [SukiSU-Ultra/SukiSU-Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra) |
| **SUSFS** | [simonpunk/susfs4ksu](https://gitlab.com/simonpunk/susfs4ksu) |

</div>

---

## 🔗 Useful resources

- [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)
- [WildKSU Manager](https://github.com/WildKernels/Wild_KSU/releases)
- [KernelSU](https://kernelsu.org/)
- [KernelSU Next](https://kernelsu-next.github.io/webpage/)
- [SUSFS](https://gitlab.com/simonpunk/susfs4ksu)
- [SukiSU Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
- [ReSukiSU](https://github.com/ReSukiSU/ReSukiSU)

---

## 💝 Donations

Any and all donations are appreciated!

- **PayPal:** [paypal.me/fatalcoder524](https://paypal.me/fatalcoder524)
- **UPI donations:** DM on Telegram

---

## 🙏 Credits

This fork is based on work from:

- **WildKernels** — original OnePlus KernelSU SUSFS workflow and kernel patch ecosystem  
  [WildKernels/OnePlus_KernelSU_SUSFS](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS)
- **KernelSU Team**
- **KernelSU Next Team**
- **ReSukiSU Team**
- **SukiSU Ultra Team**
- **simonpunk** — SUSFS development
- **fatalcoder524** — Kernel Flasher and community Android kernel tools
- **OnePlus / Oppo / Realme** — kernel source releases
- Android kernel community contributors and testers

---

<div align="center">

**Built with ❤️ for advanced Android kernel users**

</div>
