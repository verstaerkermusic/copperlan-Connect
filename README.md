# Copperlan Connect — Apple Silicon public beta

<img width="1365" height="812" alt="Screenshot_2026-10-15 16 20 15_iwzy7m" src="https://github.com/user-attachments/assets/1114b416-c4d2-41bb-9e26-dbbc95685668" />



An independent MIDI routing application for CopperLAN networks on Apple Silicon
Macs. This is not an official CopperLAN or Alyseum release.

Candidate: **0.3.0-rc.15, build 18**. Beta software: save your existing hardware
configuration before testing. The app is ad-hoc signed, not notarized.

## Quick start

1. Extract the ZIP and move the **whole folder** to a permanent location.
2. Run **Setup.command**. If the helper is missing, type INSTALL and enter your admin password once.
3. Setup selects helper mode and asks whether to start automatically when you log in.
4. Open **Copperlan Connect.app**, select your Ethernet adapter in Settings and click **Start service**.

Python is included. Do not install a separate Python or disable macOS security
globally. See the detailed README inside the download for macOS approval,
existing-helper installations and removal instructions.

## Automatic startup

Stop the service, run **Enable Login Startup.command**, then start the service
again. It starts when this user logs in, not before login. Keep the installed
folder in place. Closing the app leaves the service running; deliberately stopping
the service suppresses automatic startup until you start it again.

## Routing and monitoring

Choose a source, destination and channels, then **Add route**. Select an existing
connection and **Remove route** to disconnect it. Computer ports have **Send to
network** and **Receive from network** directions. Monitor sent MIDI on the sending
port, and received MIDI on the receiving port. Detailed steps are in the app's Help.

## Requirements and limitations

- Apple Silicon Mac and Ethernet connection to the CopperLAN network.
- Administrator access for the one-time hardware helper installation.
- macOS 13 is the build minimum; runtime compatibility with every macOS version is not verified.
- Experimental hardware monitoring; previews are bounded and not a lossless MIDI recorder.
- Full-cable operations are sequential, not atomic. After an error, inspect the remaining routes.
- Network recovery is not universal: SysEx, active hardware-monitor routes and uncertain writes retain conservative safeguards.
- Original Intel services are not removed automatically. Same-Mac coexistence is not generally guaranteed; use the installation guide's testing precautions.
- Hardware Store/Restore changes device configurations; neither runs automatically.

## Tested recovery in this candidate

Two-Mac tests confirmed MIDI resumes after receiving-Mac Ethernet unplug/replug
for AL → CMidi, multiple AL → CMidi routes, and CMidi → CMidi. The MIDI monitor may
need reopening. This is test coverage, not a guarantee for every setup.

## Feedback

Report the app version, macOS version, Mac model, Ethernet adapter, source/target
ports and channels, and reproduction steps. Say whether MIDI itself stops or only
the monitor is empty. Do not post raw captures, passwords, SSH keys or unreviewed
diagnostics: logs can include device names and network identifiers.
