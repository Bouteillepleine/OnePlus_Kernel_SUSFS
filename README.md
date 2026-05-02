<div align="center">

# OnePlus ● KernelSU(N) ● SukiSU Ultra ● ReSukiSU ● SUSFS

### Wild Fork

Automated OnePlus kernel builds with KernelSU, KernelSU Next, ReSukiSU, SukiSU Ultra, and SUSFS.

[![Actions](https://img.shields.io/badge/GitHub%20Actions-Builds-blue)](../../actions)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-green)](https://github.com/tiann/KernelSU)
[![KernelSU Next](https://img.shields.io/badge/KernelSU--Next-Supported-brightgreen)](https://github.com/KernelSU-Next/KernelSU-Next)
[![ReSukiSU](https://img.shields.io/badge/ReSukiSU-Supported-blue)](https://github.com/ReSukiSU/ReSukiSU)
[![SukiSU Ultra](https://img.shields.io/badge/SukiSU%20Ultra-Supported-purple)](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-orange)](https://gitlab.com/simonpunk/susfs4ksu)

</div>

---

## ⚠️ Warning

Flashing custom kernels can brick your device or cause data loss.

Back up your data and stock `boot`, `init_boot` images before flashing.  
Only flash builds made for your exact device and OS version.

Use at your own risk.

---

## Supported

- KernelSU
- KernelSU Next
- ReSukiSU
- SukiSU Ultra
- SUSFS

---

## Build

Run from GitHub Actions:

```text
Actions → Build and Release OnePlus Kernels → Run workflow
```

Important inputs:

| Input | Description |
|---|---|
| `op_model` | OS/kernel group, e.g. `OOS16` or `android16-6.12` |
| `target_model` | Optional exact model filter |
| `ksu_options` | Root variant JSON |
| `make_release` | Publish release |

Example:

```json
[{"type":"sukisu","hash":"main"}]
```

Supported types:

```text
ksu
ksun
rsksu
sukisu
```

---

## Compatibility

Check:

```text
configs/
```

Do not flash if your exact model and OS version are not listed.

---

## Install

Recommended tool:

- [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)

Steps:

1. Download the correct AnyKernel3 ZIP.
2. Back up boot partitions.
3. Flash the ZIP.
4. Install the matching manager app.
5. Reboot.

---

## Manager Apps

| Variant | Manager / Releases |
|---|---|
| KernelSU | [KernelSU releases](https://github.com/tiann/KernelSU/releases) |
| KernelSU Next | [KernelSU Next releases](https://github.com/KernelSU-Next/KernelSU-Next/releases) |
| ReSukiSU | [ReSukiSU releases](https://github.com/ReSukiSU/ReSukiSU/releases) |
| SukiSU Ultra | [SukiSU Ultra releases](https://github.com/SukiSU-Ultra/SukiSU-Ultra/releases) |
| WildKSU Manager | [WildKSU releases](https://github.com/WildKernels/Wild_KSU/releases) |

Recommended SUSFS module:

- [KSU SUSFS Module](https://github.com/sidex15/ksu_module_susfs/releases)

---

## 💝 Donations

Any and all donations are appreciated!

- PayPal: [paypal.me/fatalcoder524](https://paypal.me/fatalcoder524)
- DM on Telegram for UPI donations!

---

## Credits

Thanks to WildKernels, KernelSU, KernelSU Next, ReSukiSU, SukiSU Ultra, SUSFS, fatalcoder524, OnePlus/Oppo/Realme, and the Android kernel community.

---

<div align="center">

**Flash enjoy!**

</div>
