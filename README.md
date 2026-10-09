# 🛠️ Keil MDK-ARM + LPC1700_DFP 2.7.2 — Installation Guide (Windows)

A beginner-friendly, step-by-step guide (A → Z) for students who need **Keil MDK-ARM (µVision)** and the **LPC1700 Device Family Pack (DFP) v2.7.2** for an LPC1700-based course or lab.

> ✅ **Tested setup:** Keil MDK-ARM **5.43a** + `Keil.LPC1700_DFP.2.7.2.pack` on Windows
> ⚠️ **Note:** The official Keil pack page labels LPC1700_DFP 2.7.2 as *deprecated / no longer maintained*. If your course requires **exactly 2.7.2**, install that version and do **not** replace it with a newer one.

> 📌 **Disclaimer:** This is an unofficial, student-made guide. It is **not affiliated with, endorsed by, or sponsored by Arm, Keil, or NXP**. Always follow the official documentation and your instructor's instructions if they differ from this guide.

---

## 📑 Table of Contents

1. [What you need](#1--what-you-need)
2. [Before you start (checklist)](#2--before-you-start-checklist)
3. [Step 1 — Download Keil MDK-ARM](#3--step-1--download-keil-mdk-arm)
4. [Step 2 — Install Keil MDK-ARM](#4--step-2--install-keil-mdk-arm)
5. [Step 3 — Download LPC1700_DFP 2.7.2](#5--step-3--download-lpc1700_dfp-272)
6. [Step 4 — Import the pack into Keil](#6--step-4--import-the-pack-into-keil)
7. [Step 5 — Verify the installation](#7--step-5--verify-the-installation)
8. [Step 6 — Create your first LPC1700 project](#8--step-6--create-your-first-lpc1700-project)
9. [Step 7 — Build (compile) test](#9--step-7--build-compile-test)
10. [Troubleshooting: errors and solutions](#10--troubleshooting-errors-and-solutions)
11. [Quick checklist](#11--quick-final-checklist-)
12. [FAQ](#12--faq)
13. [References and credits](#13--references-and-credits)
14. [Legal notice and license](#14--legal-notice-and-license)

---

## 1. 📦 What you need

| # | Item | What it is | Where to get it |
|---|------|-----------|-----------------|
| 1 | **Windows PC** | Windows 10 / 11 (64-bit recommended) | — |
| 2 | **Keil MDK-ARM** | IDE (µVision), compiler, debugger | [keil.com/download/product](https://www.keil.com/download/product/) |
| 3 | **LPC1700_DFP v2.7.2** | Device Family Pack: device data, headers, startup files, flash algorithms for NXP LPC1700 | [keil.arm.com/packs/lpc1700_dfp-keil/versions](https://www.keil.arm.com/packs/lpc1700_dfp-keil/versions/) |
| 4 | **Internet connection** | For the downloads | — |
| 5 | **Administrator rights** | Needed to install software on most PCs | — |

**What does DFP mean?** *DFP = Device Family Pack.* It tells Keil everything about a family of microcontrollers (device list, registers/header files, startup code, flash programming algorithms, debug description).

---

## 2. ✅ Before you start (checklist)

- [ ] You know the **exact MCU** used in your lab (for example *LPC1768* — "LPC1700" is only the family name).
- [ ] You know which **MDK version** your course requires (if not specified, 5.43a is the tested one here).
- [ ] You have **at least ~2–3 GB** of free disk space.
- [ ] You can **run installers as administrator**.
- [ ] You have temporarily checked that your antivirus will not block the installer.

---

## 3. ⬇️ Step 1 — Download Keil MDK-ARM

1. Open the official download page: <https://www.keil.com/download/product/>
2. Select **MDK-Arm**.
3. Fill in the registration form if requested (Keil may ask for name, e-mail, etc.).
4. Download the Windows installer (`.exe`). Example used in this guide:

```text
MDK543a.exe
```

> 💡 If your course provides a specific MDK version or installer, use **that one**.

![Keil download page](images/01-keil-download-page.png)
*(Screenshot placeholder: Keil MDK-Arm download page.)*

---

## 4. 💿 Step 2 — Install Keil MDK-ARM

1. **Right-click** the installer → **Run as administrator**.
2. Click **Next**.
3. Accept the license agreement → **Next**.
4. Choose the installation folder (see the table below).
5. Fill in your name / e-mail if asked → **Next**.
6. Wait for the installation, then click **Finish**.
7. If Windows asks to install **drivers** (ULINK, ST-Link, etc.), you can accept them — they are useful when you connect a board.

### 📁 Recommended installation folder

| Option | Example path | Recommendation |
|--------|--------------|----------------|
| ✅ Simple path, **no spaces** | `D:\Keil` or `C:\Keil` | **Best** |
| ⚠️ Default path with spaces | `C:\Program Files\Keil` | Works for most users, but may cause problems with older tools/projects |

If the installer asks for two folders:

```text
Core: D:\Keil
Pack: D:\Keil
```

> ⚠️ **Avoid** paths with spaces, accents or special characters (for example `C:\Users\Mario Rossi\...` or `C:\Università\...`) for the install folder **and** for your project folders.

![Keil installer folder selection](images/02-keil-installer-folders.png)
*(Screenshot placeholder: installer folder selection screen.)*

### Open µVision for the first time

Start menu → **Keil µVision5**. If it opens correctly, the base installation is done. ✅

---

## 5. ⬇️ Step 3 — Download LPC1700_DFP 2.7.2

1. Open: <https://www.keil.arm.com/packs/lpc1700_dfp-keil/versions/>
2. Find the row:

```text
LPC1700_DFP — Version 2.7.2
```

3. Download the file:

```text
Keil.LPC1700_DFP.2.7.2.pack
```

![LPC1700_DFP versions page](images/03-lpc1700-dfp-versions.png)
*(Screenshot placeholder: versions list with 2.7.2 highlighted.)*

### 🔎 Make sure you pick the right file

| ✅ Correct | ❌ Wrong (different packs) |
|-----------|---------------------------|
| `Keil.LPC1700_DFP.2.7.2.pack` | `ARM.Cortex_DFP.x.x.x` |
| | `ARM.CMSIS.x.x.x` |
| | `Keil.MDK-Middleware.x.x.x` |
| | `Keil.LPC1700_DFP.2.7.x` (a different version number) |

---

## 6. 📥 Step 4 — Import the pack into Keil

There are **two ways**. Use whichever works for you.

### Method A — Double-click the `.pack` file

1. Locate `Keil.LPC1700_DFP.2.7.2.pack` (usually in `Downloads`).
2. Double-click it.
3. **Pack Installer** opens → follow the prompts → accept the license → wait until it finishes.

### Method B — Import from Pack Installer (most reliable)

1. Open **Pack Installer**
   - From µVision: `Project → Manage → Pack Installer`
   - Or from the Start menu: **Keil Pack Installer**
2. Click `File → Import...`
3. Browse to the folder with the `.pack` file.
4. Select `Keil.LPC1700_DFP.2.7.2.pack` → **Open**.
5. Wait until the status bar says it is finished.

![Pack Installer import](images/04-pack-installer-import.png)
*(Screenshot placeholder: Pack Installer → File → Import.)*

### 🔁 "The pack has already been imported or downloaded"

You may see:

```text
The pack has already been imported or downloaded.
Do you want to continue the import/installation and replace it?
```

Click **Yes** if you want to reinstall the same pack. It is **not** an error: Keil already has a copy.

### 🔍 Where is my `.pack` file?

| Location | Typical path |
|----------|--------------|
| Browser downloads | `C:\Users\<your-name>\Downloads` |
| Keil Pack Installer download folder | `D:\Keil\.Download` (depends on your install/settings; the folder is hidden-style, type the path manually in the file dialog) |
| Search | Windows Explorer → search for `Keil.LPC1700_DFP*` |

---

## 7. 🔬 Step 5 — Verify the installation

1. Open **Pack Installer**.
2. In the left panel (**Devices**), search for `LPC1700` or `LPC1768`.
3. Expand: `NXP → LPC1700 Series → LPC176x → LPC1768` (your device).
4. In the right panel (**Packs** tab), check that:

| What to check | Expected |
|---------------|----------|
| Pack name | `Keil::LPC1700_DFP` |
| Version | **2.7.2** |
| Status | **Up to date** / **Installed** |

> The LPC1700 DFP supports the NXP LPC1700 family: LPC175x, LPC176x, LPC177x and LPC178x devices.

![Pack Installer verification](images/05-pack-installer-verify.png)
*(Screenshot placeholder: LPC1700_DFP 2.7.2 shown as installed.)*

---

## 8. 🆕 Step 6 — Create your first LPC1700 project

1. Open **µVision**.
2. `Project → New µVision Project...`
3. Create a **new empty folder** (simple path, e.g. `D:\Projects\lab1`), type a name (e.g. `lab1`) → **Save**.
4. The **Select Device for Target** window opens:
   - Expand `NXP`
   - Expand `LPC1700 Series` → the subfamily (e.g. `LPC176x`)
   - Select **your exact MCU** (e.g. `LPC1768`) → **OK**
5. The **Manage Run-Time Environment** window appears:
   - Tick `CMSIS → CORE`
   - Tick `Device → Startup`
   - → **OK**
6. In the *Project* panel: right-click **Source Group 1** → `Add New Item to Group...` → **C File (.c)** → name it `main.c`.

Paste this minimal code:

```c
#include "LPC17xx.h"

int main(void)
{
    while (1)
    {
        /* your code here */
    }
}
```

![New project device selection](images/06-select-device.png)
*(Screenshot placeholder: Select Device for Target window.)*

> ⚠️ Select the **exact MCU from your lab instructions**. "LPC1700" is a family, not necessarily the chip on your board.

---

## 9. 🔨 Step 7 — Build (compile) test

1. Press **F7** or click the **Build** button.
2. Look at the **Build Output** window at the bottom.

| Result | Meaning |
|--------|---------|
| `0 Error(s), 0 Warning(s)` | ✅ Installation works |
| Errors | See the [troubleshooting section](#10--troubleshooting-errors-and-solutions) |

![Build output](images/07-build-output.png)
*(Screenshot placeholder: successful build with 0 errors.)*

---

## 10. 🧯 Troubleshooting: errors and solutions

### 10.1 Quick problem table

| # | Problem / message | Likely cause | Solution |
|---|-------------------|--------------|----------|
| 1 | Cannot find LPC1700 in the device list | Pack not installed / wrong pack imported | Re-import `Keil.LPC1700_DFP.2.7.2.pack` (see 10.2) |
| 2 | Only ARM / CMSIS packs visible | You imported or downloaded the wrong file | Download the correct file and use `File → Import` |
| 3 | "The pack has already been imported…" | Pack already present | Click **Yes** to reinstall — not an error |
| 4 | Pack Installer shows "Cannot access the Pack index / no internet" | Network, proxy, firewall or university Wi-Fi | Skip online mode: download the `.pack` in the browser and import manually (10.3) |
| 5 | Double-clicking the `.pack` does nothing / opens another program | File association is wrong | Use Method B (`File → Import`) |
| 6 | Installer fails / stops halfway | No admin rights, antivirus, corrupted download | Run as administrator, pause antivirus temporarily, re-download (10.4) |
| 7 | Build error about **Arm Compiler 5 / "toolchain not installed"** | Newer MDK no longer includes ARMCC 5 by default | Switch to Arm Compiler 6 or install the legacy compiler (10.5) |
| 8 | Wrong / newer pack version used by a project | Project set to "use latest" | Fix the pack version in the project (10.6) |
| 9 | `error: ... code size limit exceeded` (L250E) | Evaluation/size-limited license | Check your license edition (10.7) |
| 10 | µVision cannot find `LPC17xx.h` | RTE not configured / wrong device | Re-open **Manage Run-Time Environment**, tick CMSIS Core + Device Startup |
| 11 | Debugger not detected / flash download failed | Driver, cable, wrong debug adapter or wrong device | See 10.8 |
| 12 | Strange errors with project in a folder with spaces or accents | Path issue | Move the project to a simple path like `D:\Projects\lab1` |
| 13 | Pack shows "deprecated" warning | Official page marks 2.7.2 as deprecated | Normal. Keep 2.7.2 if your course requires it |
| 14 | µVision won't start / crashes | Corrupted install, antivirus, missing permission | Reinstall as administrator (10.4) |

---

### 10.2 ❌ LPC1700 devices not visible

1. Open **Pack Installer**.
2. Check the **Packs** tab for `Keil::LPC1700_DFP`.
3. If missing → `File → Import...` → select `Keil.LPC1700_DFP.2.7.2.pack`.
4. Close and reopen µVision and Pack Installer.
5. If it still fails, remove and re-import:
   - In Pack Installer → Packs tab → right-click the pack → **Remove** (if listed)
   - Import again.

### 10.3 🌐 Pack Installer cannot download / "no internet"

Use the manual method:

```text
Download .pack in your browser
        ↓
Open Pack Installer
        ↓
File → Import...
        ↓
Select Keil.LPC1700_DFP.2.7.2.pack
        ↓
Open
```

Other ideas:
- Try another network (mobile hotspot instead of university Wi-Fi).
- Temporarily disable VPN/proxy.
- Check your firewall.

### 10.4 🛡️ Installer problems

| Try this | Why |
|----------|-----|
| Right-click → **Run as administrator** | Needed to write in the install folder |
| Re-download the installer | The file may be corrupted |
| Pause antivirus/Defender real-time protection **temporarily** | Some antivirus tools block installers/drivers |
| Install to `D:\Keil` or `C:\Keil` | Avoid permission/space problems |
| Restart Windows and try again | Clears locked files |
| Close all other Keil programs | Avoid file locks |

> 🔒 Re-enable your antivirus right after the installation.

### 10.5 ⚙️ Compiler error: Arm Compiler 5 not found

Typical symptom (wording can vary):

```text
Error: C9555E: Toolchain not found / Compiler version 5 not installed
```

**Why:** older lab projects were created with **Arm Compiler 5 (ARMCC)**, but recent MDK versions do not install it by default.

**Solution A — Switch the project to Arm Compiler 6 (usually the easiest):**
1. `Project → Options for Target...` (or press **Alt+F7**)
2. Tab **Target**
3. **ARM Compiler:** choose **Use default compiler version 6** (or a version 6 listed)
4. **OK** → rebuild
5. If the project has old code, you may see new warnings or errors — ask your instructor.

**Solution B — Install the legacy compiler:** if your course requires Arm Compiler 5, follow the instructions from your course or the official Arm/Keil documentation on legacy compiler support.

### 10.6 📌 Project uses the wrong pack version

1. `Project → Manage → Select Software Packs...`
2. For `Keil::LPC1700_DFP`, **untick** "Use latest version of all installed Software Packs" and select version **2.7.2** explicitly.
3. **OK** → rebuild.

### 10.7 🔑 Code size limit / license issues

| Symptom | What to do |
|---------|-----------|
| Build fails with a "code size limit" error | Your installation may be a size-limited evaluation edition |
| License questions | Read the license terms on the official Keil site and use the edition offered for your situation (e.g. a free community/educational option, if available) |
| University provides licenses | Follow your university's/instructor's instructions |

> 🧾 Do **not** use cracks, keygens or "patched" installers. They are illegal, unsafe, and not covered by this guide.

### 10.8 🔌 Debugger / flash errors (when you connect a board)

| Symptom | Things to check |
|---------|-----------------|
| "No target connected" / "No ULINK/CMSIS-DAP device found" | USB cable (use a data cable), try another USB port, reinstall drivers |
| "Flash Download failed – Cortex-M3" | Wrong device selected, or board not powered, or wrong flash algorithm |
| Debug works on one PC but not another | Driver differences — reinstall the debug adapter driver |
| Wrong debugger selected | `Project → Options for Target → Debug` → choose the adapter used in your lab |
| Board not recognised | Check power jumper/LED, try another cable |

---

## 11. ✅ Quick final checklist

- [ ] Windows PC
- [ ] Keil MDK-ARM installed
- [ ] µVision opens successfully
- [ ] Pack Installer opens successfully
- [ ] `Keil.LPC1700_DFP.2.7.2.pack` downloaded
- [ ] LPC1700_DFP **2.7.2** imported
- [ ] LPC1700 devices visible in Pack Installer
- [ ] Exact MCU selectable in a new project
- [ ] Test project builds with **0 errors**

If all boxes are checked, your Keil environment is ready. 🎉

---

## 12. ❓ FAQ

**Q: Do I need the LPC1700 pack if I already installed MDK?**
A: Yes. MDK does not include every device family by default. The DFP adds the LPC1700 devices.

**Q: Can I install a newer DFP instead of 2.7.2?**
A: Only if your instructor says so. Some labs depend on this specific version.

**Q: Which Windows versions are supported?**
A: This guide was tested on Windows. Check the official Keil site for the current system requirements.

**Q: Can I use macOS or Linux?**
A: Keil µVision is a Windows application. Ask your instructor about alternatives (e.g. a Windows virtual machine).

**Q: Where are the pack files stored?**
A: Usually inside your Keil folder (e.g. `D:\Keil\ARM\PACK\Keil\LPC1700_DFP\2.7.2`). The exact path depends on your settings.

---

## 13. 📚 References and credits

All product information in this guide comes from the official sources below. Please consult them for the most up-to-date details.

| Resource | Link |
|----------|------|
| Keil Product Downloads | <https://www.keil.com/download/product/> |
| Keil LPC1700_DFP versions | <https://www.keil.arm.com/packs/lpc1700_dfp-keil/versions/> |
| Keil MDK Getting Started Guide | <https://www.keil.com/support/man/docs/mdk_gs/> |
| Keil MDK Support | <https://www.keil.arm.com/support/> |
| Keil CMSIS Packs | <https://www.keil.arm.com/packs/> |

**Credits**
- Keil, µVision and MDK are products/trademarks of **Arm Limited** (and/or its affiliates).
- NXP and LPC are trademarks of **NXP Semiconductors**.
- Windows is a trademark of **Microsoft Corporation**.
- All trademarks belong to their respective owners.

---

## 14. ⚖️ Legal notice and license

- This repository contains **only written instructions**. It does **not** include, redistribute or mirror any Keil/Arm installer, `.pack` file, license key, or other proprietary software. Download everything from the official links above.
- Screenshots (if added) are taken by the author of this guide for educational purposes. Do not upload screenshots that contain license keys, personal data or e-mail addresses.
- The text of this guide is provided **"as is"**, without warranty. Use at your own risk.
- Suggested license for this guide's text: **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** (or MIT — choose one and add a `LICENSE` file to your repository).

---

## 🤝 Contributing

Found a mistake or a new error with a fix? Open an **Issue** or a **Pull Request**. Student-to-student help is welcome.

*This guide is a practical student-to-student reference. Always follow the official Keil/Arm documentation and your course instructions if they differ.*
