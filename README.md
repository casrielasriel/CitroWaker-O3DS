## CitroWaker o3DS

A fork of CitroWaker specialized for o3DS with stable performance on New aswell.

> **There is quite literally nothing new yet.** I haven't pushed anything YET but i AM working on it.

## The project
*AI DISCLAIMER*

***From Upstream:*** Codex and Claude Code were used for a solid chunk of this, as a college student i literally do not have the time to do it all alone.

As for the fork itself, I will be attempting to keep myself AWAY from AI usage with this, but it MAY be used considering my C++ skills are not too great with all the new stuff it has over C (classes..)

## Install in three steps (From Upstream)

**You need:** a **New** 3DS / 3DS XL / 2DS XL with custom firmware and [FBI](https://github.com/Steveice10/FBI), and **your own** USA disc image of *The Wind Waker* (`GZLE01`, plain `.iso`). Nothing from the game is downloaded or included.

<table>
<tr>
<td width="55%">

1. **Download one file** for your PC from [**Releases**](https://github.com/AureoLightz/CitroWaker/releases):
   **Windows** `CitroWaker-Installer.exe` · **Linux** `CitroWaker-Installer-linux-x86_64`
2. **Run it**, choose your disc image, plug in your SD card and press **Install**. The game is built into the installer.
3. **On the 3DS**, open **FBI › SD › cia › `CitroWaker.cia` › Install CIA**, then start **CitroWaker** from the HOME Menu.

**Updating?** Download the new installer and run it again. Your saves are kept and the disc image is not copied twice.

<sub>[Installer details & command line →](installer/README.md)</sub>

</td>
<td width="45%" align="center">
<img src="assets/installer.png" alt="The CitroWaker Installer window: disc image and SD card steps with an Install button" width="100%"><br>
<sub>The installer (Linux shown; Windows looks the same).</sub>
</td>
</tr>
</table>

The original 3DS and 2DS are not supported. Wrong-region, later-revision, trimmed or compressed (RVZ/CISO) images are rejected with instructions to fix them.

## The bottom screen

<table>
<tr>
<td width="50%" align="center">
<img src="assets/bottom-panel.png" alt="CitroWaker bottom screen: a Settings button on the left and X, Y, Z, Menu and Map touch buttons on the right" width="100%"><br>
<strong>Touch panel</strong><br>
<sub>Touch X, Y or Z to use the assigned item, Menu for the pause menu, Settings for CitroWaker's options.</sub>
</td>
<td width="50%" align="center">
<img src="assets/bottom-livemap.png" alt="CitroWaker bottom screen showing the game's live map next to the touch buttons" width="100%"><br>
<strong>Live map</strong><br>
<sub>Optional: the game's minimap drawn on the bottom screen (<i>Settings › Bottom screen</i>).</sub>
</td>
</tr>
</table>

Buttons follow the game's own HUD: usable when the game allows the action, greyed out in cutscenes and conversations. **START + SELECT** opens the settings menu anywhere; changes are saved to the SD card. [Controls →](docs/DEVELOPMENT.md#controls) &nbsp; · &nbsp; [QoL & gyro →](QOL.md) &nbsp; · &nbsp; [Touch shortcuts →](SHORTCUTS.md)

## Development status

| Area | Current state |
| :--- | :--- |
| **Game & audio** | Boots and reaches gameplay on real New 3DS; sound and physical controls run. |
| **Graphics** | Custom GX-to-PICA renderer. Some console depth, cloud and shadow faults remain under investigation. |
| **Performance** | Not yet at speed: heavy scenes on console measure about 12 fps (80 ms frames); the GPU command translation is the bottleneck and the main focus. Console numbers in [Performance](docs/PERFORMANCE.md); emulator FPS is not console FPS. |
| **Saving** | SD-backed memory cards; the settings menu now saves on hardware. Keep backups of `/3ds/ww3ds/user/`. |
| **Touch & QoL** | Bottom-screen touch panel and optional live map; QoL and gyro options are opt-in. |
| **Release** | Installer, CIA, port sources and host tests published. |

### Where we're heading

1. **Every-frame performance:** a constant 30 fps on console by cutting command decoding, memory traffic and draw preparation.
2. **Correctness and stability:** console rendering faults and scene-change stalls.
3. **Handheld polish:** live map on by default once its video memory cost is gone.

## Source and tools

| Component | Start here |
| :--- | :--- |
| **Installer** | [Windows/Linux GUI and command line](installer) |
| **Port source** | [3DS game layer, renderer and citro3d changes](port) |
| **3DS platform code** | [NDSP audio, touch/lifecycle logic and configuration](platform/n3ds) |
| **PC texture converter** | [Buildable extractor and converter](tools/texture-pack): process your own ISO locally. |
| **Console log reports** | [Summarize and compare timings](tools/console-report) |
| **Host tests** | `python3 tests/run.py` with Python 3.10+ and a C++17 compiler (`--python-only` for the Python tests). |

[Source scope, dependencies & licence →](docs/SOURCE.md) &nbsp; · &nbsp; [Player-release notes →](docs/PLAYER_RELEASE.md)

## Beyond Outset

The ending cutscene also boots and renders in the port. This development capture includes a measured frame-time graph beneath the game picture.

<p align="center">
  <img src="assets/ending-timing.png" alt="The ending cutscene with Link and Tetra, captured in Azahar with an emulator frame-time graph below" width="86%">
</p>

<sub>Azahar capture · The displayed timing is emulator/virtual timing, not console FPS. The Ganondorf battle has not been captured.</sub>

The [Python + FFmpeg showcase tool](tools/showcase/README.md) adds timing graphs to existing footage. It distinguishes emulator, console and host measurements and does not invent timings from the video's frame rate.

## Follow the work

| For players | For developers |
| :--- | :--- |
| [Install with the installer](#install-in-three-steps) | [Development arrangement](docs/DEVELOPMENT.md#building-from-source) |
| [QoL & gyro settings](QOL.md) | [Performance measurements](docs/PERFORMANCE.md) |
| [Touch shortcut status](SHORTCUTS.md) | [Hardware findings](docs/CONSOLE_FINDINGS.md) |
| [Report an issue](https://github.com/AureoLightz/CitroWaker/issues) | [Timing-overlay tool](tools/showcase/README.md) |

Bug reports are most useful with the build identifier, console/emulator details, scene and reproduction steps. Review diagnostics for personal information; never attach an ISO or extracted game-data pack.

---

<p align="center"><strong>Built on the community's work</strong></p>
<p align="center">
  <a href="https://github.com/zeldaret/tww">zeldaret/tww</a> &nbsp; · &nbsp;
  <a href="https://github.com/centollOS/SwitchWaker">SwitchWaker</a> &nbsp; · &nbsp;
  <a href="https://github.com/encounter/aurora">Aurora</a> &nbsp; · &nbsp;
  <a href="https://devkitpro.org/">devkitPro</a> &nbsp; · &nbsp;
  <a href="https://github.com/azahar-emu/azahar">Azahar</a>
</p>

<sub>The Legend of Zelda and The Wind Waker belong to Nintendo. CitroWaker is an independent community project, not affiliated with or endorsed by Nintendo. Screenshots contain game imagery; original project code is MIT-licensed, with no licence over Nintendo assets granted. See [repository scope and rights](RIGHTS.md).</sub>
