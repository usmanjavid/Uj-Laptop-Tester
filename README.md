# Uj Laptop Tester

**A portable laptop diagnostics toolkit for Windows, Intel Macs, and Apple Silicon Macs.**

Check battery capacity, storage health, keyboard input, display quality, audio, and more from one modern interface. Run CPU/GPU workloads, verify an allocated area of memory, and record your observations in an exportable report.

Created by **Usman Javed / UJMix** · [ujmix.com](https://ujmix.com/)

> Hardware support varies. Some checks are automatic; others require a connected peripheral or your observation. A passed test does not guarantee that a device is fault-free or predict its remaining lifespan.

## Downloads

Open the **Releases** section of this repository and choose the asset for your computer.

| Platform | Release asset | Requirements |
|---|---|---|
| Windows | `Uj-Laptop-Tester-3.0-Windows-x64.zip` | Windows 10 or 11, x64 |
| macOS — Intel | `Uj-Laptop-Tester-3.0-macOS-Intel.zip` | macOS 12 Monterey or newer, Intel processor |
| macOS — Apple Silicon | `Uj-Laptop-Tester-3.0-macOS-Apple-Silicon.zip` | macOS 12 Monterey or newer, Apple M-series processor |

These are **three platform builds**, not three different products. The Mac downloads are separate native builds rather than a single universal application.

The required runtime and storage engine are bundled. End users do not need to install .NET, Homebrew, or a compiler.

## Features

| Test | What it does |
|---|---|
| Battery | Compares reported full-charge and design capacities where compatible values are available; shows other supported battery information. |
| SSD / HDD / NVMe | Reads supported SMART status, wear, temperature, and error information using bundled smartmontools. |
| Keyboard | Displays delivered key events and previously observed keys. |
| Display | Provides solid colors, gray, gradients, checkerboard, and motion patterns for visual inspection. |
| Speakers | Plays left, right, stereo, and frequency-sweep tones. |
| CPU | Runs timed integer and floating-point workloads with verification. |
| GPU | Runs a verified compute workload using Direct3D 11 on Windows or Metal on macOS. |
| Memory | Writes and verifies patterns within a selected process-memory allocation. |
| Webcam | Displays a local camera preview for checking focus, exposure, and picture quality. |
| Microphone | Offers short recordings, input levels, playback, and optional WAV export. |
| Touchpad / trackpad | Shows pointer movement, clicks, scrolling, and supported gesture events. |
| Ports and peripherals | Shows connected hardware and helps you inspect USB, USB-C, display, Ethernet, and audio connections. |
| Wi-Fi and Bluetooth | Reads available adapter/device information, opens system pairing controls, and offers a local-gateway check. |
| Sensors | Shows supported thermal and fan information; the data available differs by platform and hardware. |
| Reports | Exports readings and recorded manual observations to a text file. |

## Getting started

### Windows

1. Download the Windows x64 EXE from **Releases**.
2. Open it directly. No installer or command-script launcher is required.
3. Approve administrator access for drive diagnostics.
4. Start with battery, storage, keyboard, screen, and audio checks.
5. Save your work before starting a load test.

### macOS

1. Download the ZIP for **Intel** or **Apple Silicon**.
2. Extract it with macOS Archive Utility.
3. Open **Uj Laptop Tester.app**. Copying it to Applications is optional.
4. Allow camera or microphone access when you choose those tests.
5. Detailed storage and sensor checks may offer a macOS administrator prompt.

Keep the `.app` bundle intact. It contains its own runtime and diagnostic engine.

#### First-launch approval on macOS

If macOS blocks the first launch, approve the app through **System Settings → Privacy & Security → Open Anyway**:

1. Try opening **Uj Laptop Tester.app** once so macOS can display its alert.
2. Open **System Settings → Privacy & Security** and scroll to the **Security** section.
3. Find the message about Uj Laptop Tester and click **Open Anyway**, when offered.
4. Click **Open** in the confirmation dialog and authenticate if prompted.

After approval, you can open the app normally by double-clicking it.

## Suggested inspection order

1. Read battery and storage information.
2. Press the keyboard keys and test pointer movement.
3. Inspect the screen's colors, uniformity, and black background.
4. Check speakers, webcam, and microphone.
5. Attach known-good peripherals to the ports you want to inspect.
6. Run a short CPU, GPU, or memory test when ready.
7. Export a report for your records.

The **Stop active tests** control remains available while navigating the app. Runs have time limits; stopping an in-flight GPU command may take longer than stopping a CPU loop.

## Understand the results

- **Battery health is an estimate.** It depends on firmware-reported capacity values and calibration. Charge percentage and capacity health are different measurements.
- **SMART is not a guarantee.** A healthy report does not rule out every fault or prevent sudden failure. Keep backups.
- **Unavailable is not a pass or a failure.** A controller, USB bridge, driver, permission, or firmware limitation may hide a reading.
- **Memory checks cover the selected allocation.** They cannot test all memory owned by the operating system, certify every module, or identify a particular physical DIMM from a process address.
- **A short stress test has a limited scope.** Completion covers the selected workload and duration, not every application or game. Work-unit rates are not standardized benchmark scores.
- **Thermal stopping needs a valid, recent reading.** Exact die temperatures and fan RPM are not exposed on every device. Clock reductions alone do not diagnose thermal throttling.
- **Some input is handled by the operating system.** Fn keys, reserved shortcuts, and system trackpad gestures may not reach the app.
- **Ports need physical checks.** Enumeration alone cannot certify an empty socket, USB-C charging/power delivery, every connector, or its full bandwidth.
- **Several checks are manual.** Dead pixels, backlight bleed, camera quality, sound clarity, and real peripheral operation need your observation.

### Platform differences

Windows uses Direct3D 11 for GPU testing and LibreHardwareMonitor for supported sensors. Some CPU or motherboard readings depend on existing PawnIO/vendor support; the app does not install a monitoring driver.

macOS uses native Metal, AVFoundation, and available macOS hardware reports. Detailed thermal sampling uses an optional authorized `powermetrics` query. Intel and Apple Silicon may expose different sensor fields. Hackintosh behavior additionally depends on its ACPI, graphics, audio, and battery implementation.

## Privacy

- No app telemetry or automatic update service.
- Camera and microphone tests start only when requested and stop when leaving their page.
- Recordings remain local unless you explicitly save or share them. The Mac version uses a private temporary folder and deletes it on normal exit.
- Audio recordings are not included in diagnostic text reports.
- Website and system settings links open on click.
- The local-gateway check sends packets only when requested; it is not an internet speed test.
- Some hardware reports may contain device identifiers. Review reports before sharing them publicly.

## Current validation status

| Build | Status |
|---|---|
| Windows x64 | Reported working on Windows 11 by the project creator. This does not certify every feature on every device. |
| macOS Intel | Cross-compiled test build. Shared-code and packaging checks completed; real Intel Mac launch and hardware validation remain pending. |
| macOS Apple Silicon | Cross-compiled test build. Shared-code and packaging checks completed; real Apple Silicon launch and hardware validation remain pending. |

Build-time checks included CPU/memory workloads, audio generation, relevant parsing tests, and UI rendering checks. Architecture and package-integrity checks are separate from testing on physical hardware.

## Reporting a problem

Open an issue with:

- App version and downloaded asset name.
- Computer model, processor architecture, and operating-system version.
- The test involved, steps to reproduce, and exact error message.
- A screenshot or relevant report excerpt with private identifiers removed.

For layout issues, include your display resolution and scaling setting. Do not post passwords, unrelated personal information, or private recordings.

## Source and third-party notices

Use **Sources / licenses** in the app to export the supplied source and license archive. On macOS, it is also available inside the app at `Contents/Resources/Sources.zip`.

Bundled dependencies have their own licenses. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) and the full notices/source material included with the matching release. Preserve these when redistributing a release.

If you modify the app, provide the notices and any corresponding source or relinking materials required by the dependencies you distribute. Review the actual package versions and license files rather than assuming every component has the same license.

## License

The project's original application code is intended to be published under the **MIT License**, once adopted in the repository's `LICENSE` file. This statement does not relicense bundled third-party components. Those retain their own terms, including GPL, LGPL, and MPL obligations where applicable.

This software is provided without warranty. Use readings and test results as diagnostic information, not a guarantee of hardware condition.

## Credits

Created by **Usman Javed / UJMix**.

Visit [ujmix.com](https://ujmix.com/) for project information and updates.
