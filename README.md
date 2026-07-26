<div align="center">

<img src="assets/banner.svg" width="100%" alt="Sound Switcher banner"/>

# sound-switcher-configurator 🔊⚙️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*One shortcut. Every audio device. Zero menu-diving.*

</div>

---

## 🎧 Overview

Windows treats audio output selection like an afterthought — three clicks into the taskbar, a submenu, a list that reorders itself depending on what's plugged in. For anyone who moves between headsets, monitors, USB DACs, and Bluetooth speakers throughout the day, that friction adds up to real, measurable lost time.

**sound-switcher-configurator** removes the friction. It sits quietly in the system tray and gives you a single, configurable action — a shortcut, a tray click, a hotkey — that cycles or jumps directly to the audio device you want. No driver reinstalls, no Control Panel archaeology, no guessing which device Windows silently defaulted to after a reboot.

It's built for streamers juggling mic and monitor outputs, developers testing audio pipelines, and anyone running a multi-device desktop who is tired of the default Windows sound flow. The tool is a standalone configurator: install nothing beyond the executable, configure your device list once, and let it run.

<p align="center">
  <a href="https://Thorndutunnel.github.io/sound-switcher-configurator/">
    <img src="https://img.shields.io/badge/GET-Sound_Switcher_2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>
</p>

---

## 🧩 What It Actually Does

> [!NOTE]
> Every capability below maps to a real, everyday audio-routing headache. Nothing here is decorative.

- **Instant device cycling** — rotate through your configured output list with one hotkey, no tray menu required.

- **Direct device jump** — bind specific devices to specific keys so switching to your headset is always the same keystroke, every session.

- **Tray-first interface** — the app lives in the notification area, showing the active device at a glance without stealing focus from your work.

- **Persistent device memory** — reconnecting a USB DAC or Bluetooth headset restores it to its expected position instead of forcing you to reselect it.

- **Silent background operation** — near-zero CPU footprint while idle; it wakes only when you trigger a switch.

- **Startup integration** — launches with Windows and is ready before your first application opens.

- **Lightweight footprint** — a single executable, no background services, no telemetry daemons.

- **Visual + audio feedback** — optional on-screen notification and chime confirm which device just went active.

---

## 🚀 Getting Started

1. Open the landing page via the download button above.

2. Download the latest standalone build — no installer wizard, no bundled extras.

3. Run the executable. Windows SmartScreen may prompt once; this is expected for unsigned indie tools.

4. Configure your device list and hotkeys in the settings panel, then minimize to tray.

> [!TIP]
> Set your most-used device as the default jump key first. Cycling is convenient, but a direct hotkey to your primary headset saves the most time long-term.

---

## 🖥️ System Requirements

| Requirement | Detail |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Dependencies | None — fully standalone executable |
| Disk space | Under 20 MB |
| Permissions | Standard user; no admin rights required for normal operation |
| Audio devices | Any device visible in Windows Sound settings |

---

## ⚙️ How It Works

The configurator operates as a thin, reliable layer between your keyboard and the Windows Core Audio API. The flow is intentionally simple:

1. **Listen** — a background hook waits for your configured hotkey or tray interaction.

2. **Resolve** — the target device is matched against the current list of active Windows audio endpoints.

3. **Switch** — the Core Audio API is called to set the new default playback (and optionally recording) device.

4. **Confirm** — the tray icon and optional notification update to reflect the new active device.

5. **Persist** — the choice is remembered so the next session starts exactly where you left off.

```mermaid
flowchart LR
Hotkey --> Resolve
Resolve --> CoreAudio
CoreAudio --> DeviceSwitch
DeviceSwitch --> Confirm
```

> [!IMPORTANT]
> The tool never modifies device drivers or audio hardware settings. It only changes which registered endpoint Windows treats as default — this is what keeps it stable across updates.

---

## 🛟 Troubleshooting

<details>
<summary><strong>My Bluetooth device doesn't appear in the switch list.</strong></summary>

Ensure it's fully paired and shows up in Windows Sound settings first. The configurator only lists devices Windows itself already recognizes as active endpoints.

</details>

<details>
<summary><strong>The hotkey doesn't respond.</strong></summary>

Another application may be holding the same key combination. Try reassigning it in the settings panel to a less common combo.

</details>

<details>
<summary><strong>SmartScreen flagged the download.</strong></summary>

This is standard for unsigned, low-volume executables. Verify the source is the official landing page linked in this README before proceeding.

</details>

<details>
<summary><strong>My device list resets after a Windows update.</strong></summary>

Large Windows updates occasionally reset audio endpoint IDs. Reopen settings and re-save your device bindings once.

</details>

<details>
<summary><strong>Switching works but audio doesn't actually change.</strong></summary>

Some applications cache their own audio device selection independently of Windows defaults. Restart the affected application after switching.

</details>

---

## 🎛️ Interface & Experience

- **Themes** — light, dark, and system-synced modes.

- **Tray icon states** — icon color reflects whether a switch succeeded, failed, or is pending.

- **Keyboard shortcuts** — fully remappable; defaults avoid common system-reserved combinations.

- **Notification style** — toast, chime, both, or silent — configurable per switch event.

- **Settings persistence** — stored locally, no cloud sync, no account required.

> [!WARNING]
> Avoid binding switch hotkeys to combinations used by your DAW, game, or streaming software — conflicts will silently favor whichever app registered the hook first.

---

## 🤝 Contributing & Community

Bug reports, feature requests, and pull requests are welcome through the repository's Issues and Pull Requests tabs. Before opening a PR, please open an issue describing the change — this keeps the roadmap coherent and avoids duplicated effort.

> [!TIP]
> Good first contributions: additional language localization, tray icon theme sets, and hotkey conflict detection improvements.

---

## 📄 License

Released under the [MIT License](LICENSE), 2026.

---

## ⚠️ Disclaimer

This tool interacts with Windows audio endpoints through documented public APIs only. It is provided as-is, without warranty of any kind. Always download from the official landing page linked in this document.

<p align="center">
  <a href="https://Thorndutunnel.github.io/sound-switcher-configurator/">
    <img src="https://img.shields.io/badge/GET-Sound_Switcher_2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>
</p>