# XPortal

Run a full Linux desktop on any Android phone. Not a terminal. Not an emulator. A complete desktop environment with direct kernel access -- VS Code, Blender, Metasploit, local AI, all of it.

Connect your phone to a monitor and it becomes a Linux PC. Unplug it and your entire setup comes with you.

> [!IMPORTANT]
> DroidDesk is an independent GPL-3.0 open-source project that incorporates
> modified Termux:X11 components. It is not affiliated with or endorsed by
> Termux, Termux:X11, TUR, Canonical, or Ubuntu.
>
> - **Source and licenses:** <https://github.com/orailnoor/DroidDesk>
> - **Termux:X11 upstream:** <https://github.com/termux/termux-x11>

## Video

[![Watch the video](https://img.youtube.com/vi/QCr4WWsfVv8/maxresdefault.jpg)](https://youtu.be/QCr4WWsfVv8)

## What This Actually Runs

Everything below has been tested and confirmed working:

- **LibreOffice** -- Word processing, spreadsheets, presentations. Fully functional.
- **VS Code** -- Full version. Python, PIP, extensions, everything.
- **Claude Code** -- AI coding agent running directly in terminal.
- **Blender** -- Installs and opens. Laggy on mobile hardware, but it runs.
- **Wireshark** -- Full network analysis, every packet and protocol.
- **Metasploit** -- Pentesting framework, runs fine.
- **Local AI** -- Offline LLM inference, 5+ tokens/second, no API needed.
- **Firefox** -- Runs so smooth
If it runs on Ubuntu, it runs here.

## How It Works

The Linux environment runs through Termux with direct access to the phone's kernel. No emulation, no translation -- native performance.

The setup script installs a full desktop (XFCE4/LXQt/MATE/KDE) inside Termux using the Termux User Repository (TUR) for GUI apps. For tools not available in TUR (Wireshark, Metasploit, etc.), a Proot container provides a standard Ubuntu/Debian/Kali environment where you install anything with `apt`.

The automatic menu sync scans what you install inside Proot and adds it directly to your desktop app menu. No need to enter the container every time.

## DroidDesk App (Standalone)

DroidDesk is also available as a standalone Android application that completely automates this process without requiring a separate Termux installation. It renders through an embedded Termux:X11 server running in its own Android process; the app does not use VNC.

- **Rooted phones:** Run the Ubuntu filesystem through `chroot`.
- **Non-rooted phones:** Run an app-private native Termux userspace and install desktop packages from the X11 and TUR repositories. PRoot is not used.
- **Rendering:** Both modes connect directly to the embedded X11 server on `DISPLAY=:0`. Adreno devices use Turnip/Zink hardware acceleration when available; other GPUs fall back to Mesa software rendering.
- **Automated setup:** The app extracts the bundled ARM64 Termux bootstrap, configures its private package prefix, and installs the selected desktop automatically.

Download the latest release APK from the Releases tab and sideload it to begin.

## Requirements

- Any Android phone (ARM64)
- [Termux](https://f-droid.org/en/packages/com.termux/) (install from F-Droid, not Play Store)
- [Termux-X11](https://github.com/termux/termux-x11/releases/tag/nightly) (for on-phone display)

### For Monitor Output ( Optional )

**Option A: USB-C Display Output**
If your phone supports display output over USB-C, just use a USB-C to HDMI adapter. Done.

**Option B: Raspberry Pi Bridge**
For phones without display output (most mid-range phones with USB 2.0), use a Raspberry Pi Zero 2W as a bridge:
- Raspberry Pi Zero 2W with Raspberry Pi OS
- Micro USB to USB-C cable
- USB-C hub
- Micro HDMI to HDMI adapter
- SD card with Pi firmware
- Wireless keyboard and mouse

The Pi connects to the phone via USB tethering, detects the phone's IP automatically, and opens a VNC viewer to display the phone's desktop on the monitor.

## Installation

GET IT IN THE REALEASES TAB
NO LINUXY INSTALLATION STUFF REQUIRED SINCE IT IS
ALREADY SET UP AND IN THE CLOUD

## Credits

Created by [orailnoor](https://youtube.com/@orailnoor)

## License and third-party software

DroidDesk is independent software licensed under
[GNU GPL version 3 only](LICENSE). It is not affiliated with or endorsed by
Termux, Termux:X11, TUR, Canonical, Ubuntu, or other upstream projects.

The Android application incorporates GPL-licensed Termux:X11 components and
bundles other third-party software under their respective licenses. See:

- [Notices and attribution](NOTICE.md)
- [Third-party software inventory](THIRD_PARTY_NOTICES.md)
- [Release compliance status](COMPLIANCE.md)

The current compliance checklist includes unresolved source provenance,
reproducible-build, custom-prefix bootstrap, and wallpaper-license work. Do not
describe a binary release as fully compliant until the blocking checklist items
are complete.
