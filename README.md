# Copperlan Connect — Apple Silicon public beta

<img width="1365" height="812" alt="Screenshot_2026-10-15 16 20 15_iwzy7m" src="https://github.com/user-attachments/assets/1114b416-c4d2-41bb-9e26-dbbc95685668" />

An independent MIDI routing application for CopperLAN networks on Apple Silicon
Macs. This is not an official CopperLAN or Alyseum release.

Current public beta: **[0.3.0-rc.21 · Build 24](https://github.com/verstaerkermusic/copperlan-Connect/releases/tag/0.3.0-rc.21)**.
The app is ad-hoc signed, not notarized. Keep a backup of valuable hardware configurations.

## Download and installation

- **[Download the DMG](https://github.com/verstaerkermusic/copperlan-Connect/releases/download/0.3.0-rc.21/Copperlan-Connect-0.3.0-rc.21-macos-arm64.dmg)**
- [ZIP alternative](https://github.com/verstaerkermusic/copperlan-Connect/releases/download/0.3.0-rc.21/Copperlan-Connect-0.3.0-rc.21-macos-arm64.zip)
- **[Anleitung auf Deutsch (PDF)](https://github.com/verstaerkermusic/copperlan-Connect/releases/download/0.3.0-rc.21/Copperlan-Connect-rc21-Anleitung-DE.pdf)** · **[English guide (PDF)](https://github.com/verstaerkermusic/copperlan-Connect/releases/download/0.3.0-rc.21/Copperlan-Connect-rc21-Guide-EN.pdf)**
- [Full release history and changes since the previous GitHub release](https://github.com/verstaerkermusic/copperlan-Connect/releases/tag/0.3.0-rc.21) · [SHA-256 checksums](https://github.com/verstaerkermusic/copperlan-Connect/releases/download/0.3.0-rc.21/SHA256SUMS.txt)

1. Open the DMG and drag **Copperlan Connect.app** to **Applications** before opening it. For the ZIP, extract it and move the app to Applications.
2. Open the app. The guided setup asks you to select the Ethernet adapter connected to CopperLAN. If background hardware access needs installation, macOS requests administrator authorization. An existing working helper is reused.
3. Optionally enable **Start service when I log in**. There are no separate Terminal setup/start scripts for normal installation.
4. If the service remains stopped, choose the prominent **Start service** button. **Set up now** opens setup when it is still needed. Starting and device discovery are shown in the workspace.

Python and the MIDI runtime are included. No external Python, Homebrew or Xcode
is needed. If macOS blocks a trusted download because it is not notarized, follow
the app-specific Open Anyway instructions in the PDF guide; do not disable macOS
security globally.

For updates, stop the previous service and close its monitors before replacing
the app. Keep the previous package as a fallback. Use **Set up background service…**
in the app menu to confirm the adapter and optional login startup at the new location.

## Routing and monitoring

- Visual **Patch** workspace and list view, device/port search, internal routing matrices, cable labels/notes and display filters.
- Channel routes, Clock and SysEx, **Full cable**, and **MPE** cables connecting all 16 channels without SysEx or Clock.
- **CMidi 1–8** virtual port pairs and independent USB-MIDI directions selected in Settings. Computer ports expose **Send to network** and **Receive from network**.
- **MIDI Monitor** for sent/received computer MIDI and hardware inputs, including all-channel hardware monitoring. MPE and SysEx display remain incomplete.
- **MS-812** editor, assignments, modifiers, Learn and preset loading/saving. Selecting a preset alone does not load it.
- **Panic Fix** in the hardware input-port menu: a short background Full Cable connection pulse, used as a workaround for the observed OT channel-change dropout.
- **Save Routings** saves startup input routing on selected AL-88/AL-88c devices. It overwrites their saved startup routing; stop notes and allow the system a few seconds first. MS-812 presets are saved separately.

Detailed operation and shortcuts are in the app's Help and the PDF guides.

## Background service and automatic startup

Setup and removal are available from the Copperlan Connect app menu; Settings also
opens background-service setup. Only helper installation/removal needs administrator
authorization. The app and MIDI routing run as your normal user.

Closing the app leaves the MIDI service running. **Stop service** interrupts this
Mac's computer MIDI and suppresses login startup until you successfully start it
again. Hardware-to-hardware routes can remain active. Keep the app at its installed
location when login startup is enabled. See the PDF guide for removal instructions.

## Requirements and limitations

- Apple Silicon Mac and Ethernet connection to the CopperLAN network.
- macOS 13 is the build target; compatibility with every macOS version is not verified.
- Beta software, ad-hoc signed and not notarized; test your own setup before relying on it.
- Monitor previews are bounded, not a lossless MIDI recorder. MPE/SysEx display is incomplete.
- Full Cable operations are not atomic. Clock replacement may replace an existing source; removing the new cable does not restore the previous source.
- Network recovery is not universal. Uncertain writes and active hardware-monitor/SysEx cases retain conservative handling. Some stale/offline destination lists cannot yet be fully displayed.
- The historical controller identity fault is not conclusively explained. A pause/resume test without a fault was reported on rc.19; that is not a universal long-term guarantee.
- Original Intel services are not automatically removed or replaced. Hardware Store/Restore are explicit actions and do not run automatically.

The release page records the complete documented history, newest version first,
including private intermediate candidates and the changes since GitHub rc.17.

## Feedback

Report the app version/build, macOS version, Mac model, Ethernet adapter,
source/target ports and channels, and reproduction steps. Say whether MIDI itself
stops or only the display/monitor is affected. Do not post passwords, SSH keys or
unreviewed raw diagnostics: captures can contain device names and network identifiers.
