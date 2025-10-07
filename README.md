<p align="center">
  <a href="https://github.com/user-attachments/assets/53107af6-a2bb-4226-86da-e4d617b6fe96">
    <img src="https://github.com/user-attachments/assets/53107af6-a2bb-4226-86da-e4d617b6fe96" alt="Miku Pic" width="350">
  </a>
</p>

  
# Go-Bio: Windows BIOS Shortcut

This repository provides a simple Windows shortcut that lets you quickly reboot your computer directly into the BIOS/UEFI settings without needing to press any special keys (like **F2**, **Del**, or **Esc**) during startup.

---

## How It Works

The shortcut uses the built-in `shutdown.exe` tool with special flags:

```bash
"%SystemRoot%\System32\shutdown.exe" /r /fw /t 0
```

* `/r` → Restart the system
* `/fw` → Tell the firmware (UEFI) to boot into BIOS/UEFI setup on the next restart
* `/t 0` → Restart immediately (0-second delay)

---

## Usage

### Create your own shortcut

#### 1. Create the shortcut

* Right-click on your desktop → **New → Shortcut**
* Paste the following into the target box:

  ```text
  "%SystemRoot%\System32\shutdown.exe" /r /fw /t 0
  ```

#### 2. Run as Administrator

* Right-click the shortcut → **Properties → Advanced** → Check **Run as administrator**
* This is required for the `/fw` flag to work.

#### 3. Double-click the shortcut

* Your PC will immediately restart into BIOS/UEFI setup.

---

## Notes

* Works only on **UEFI systems** with supported Windows versions (**Windows 8, 10, 11**).
* On legacy BIOS systems, the `/fw` flag will be ignored.
* If you want a **1-second delay** instead, use:

  ```text
  "%SystemRoot%\System32\shutdown.exe" /r /fw /t 1
  ```
* To **cancel a pending shutdown** (if you used a delay), run:

  ```bash
  shutdown /a
  ```

---

## Disclaimer

This shortcut simply automates a Windows command.
Use at your own risk. Make sure you save all work before running it, as it will **force a restart**.
