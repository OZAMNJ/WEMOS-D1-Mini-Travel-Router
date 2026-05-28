<div align="center">

# 🌐 D1 Mini Travel Router
### *Ultimate Edition — Powered by ESP8266*

[![Release](https://img.shields.io/github/v/release/OZAMNJ/WEMOS-D1-Mini-Travel-Router?color=00d4aa&label=Latest%20Release&style=for-the-badge)](https://github.com/OZAMNJ/WEMOS-D1-Mini-Travel-Router/releases)
[![License](https://img.shields.io/github/license/OZAMNJ/WEMOS-D1-Mini-Travel-Router?style=for-the-badge&color=blue)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP8266-orange?style=for-the-badge&logo=arduino)](https://www.espressif.com/)
[![Web Installer](https://img.shields.io/badge/Web%20Installer-Available-brightgreen?style=for-the-badge)](https://ozamnj.github.io/WEMOS-D1-Mini-Travel-Router)

**Transform your $5 Wemos D1 Mini into a secure, portable travel router.**
*Beat hotel Wi-Fi restrictions. Hide all your devices. Block ads at the router level.*

[🚀 Flash Now (One Click)](https://ozamnj.github.io/WEMOS-D1-Mini-Travel-Router) · [📖 Setup Guide](#%EF%B8%8F-initial-setup--usage) · [🐛 Report Bug](https://github.com/OZAMNJ/WEMOS-D1-Mini-Travel-Router/issues) · [💡 Request Feature](https://github.com/OZAMNJ/WEMOS-D1-Mini-Travel-Router/issues)

</div>

---

## 🎯 What Is This?

This firmware turns a standard **Wemos D1 Mini (ESP8266)** into a fully functional **NAT travel router** that fits in your pocket. It is designed for travelers who need secure, private internet at hotels, airports, cafes, and Airbnbs.

| Problem | Solution |
|---|---|
| Hotel Wi-Fi only allows 1 device | Connect all your devices through 1 MAC address |
| Captive portal blocks internet | One-tap **Pause DNS** bypass mode |
| Ads and trackers on public Wi-Fi | Custom DNS blocking (NextDNS, Control D) |
| Configuration lost on reboot | **LittleFS** persistent storage |
| Slow, unresponsive dashboard | Async dark-mode UI with real-time updates |

---

## ✨ Key Features

- 🔀 **True Hardware NAT** — LwIP NAPT routes traffic between public and private networks securely
- 🏨 **Captive Portal Bypass** — "Pause DNS" toggle for seamless hotel/airport login
- 💾 **Persistent LittleFS Storage** — Configs, SSIDs, and passwords survive reboots
- 🛡️ **Custom DNS Injection** — Block ads, trackers, and malware at router level
- 🖥️ **Dark-Mode Web Dashboard** — Responsive async UI at `192.168.4.1`, no page reloads
- ⚡ **160MHz Optimised** — Double clock speed for maximum NAT throughput
- 🔒 **Password Protected** — Secure admin login for your dashboard

---

## 🛠️ Hardware Requirements

| Component | Details |
|---|---|
| **Board** | Wemos D1 Mini (ESP8266EX) |
| **Cable** | Micro-USB or USB-C **data** cable |
| **Power** | USB power bank or wall adapter |
| **Browser** | Chrome or Edge (for Web Installer) |

> **Cost:** The D1 Mini costs around $3–5 USD. This is the cheapest travel router you will ever own.

---

## 🚀 Installation

### Option A — One-Click Web Installer ✅ Recommended

> Requires Google Chrome or Microsoft Edge (WebSerial API)

1. Plug your D1 Mini into your computer via USB
2. Click the button below:

<div align="center">

**[👉 Open Web Installer](https://ozamnj.github.io/WEMOS-D1-Mini-Travel-Router)**

</div>

3. Click **Connect** → select your COM port → click **Install**
4. Wait ~30 seconds for flashing to complete

> 💡 **Not sure which COM port to select?** See the [Finding Your COM Port](#-finding-your-com-port-windows--mac--linux) 

---

### Option B — Manual Flash with esptool

```bash
# Install esptool
pip install esptool

# Flash the firmware (replace COM3 with your port)
esptool.py --port COM3 --baud 460800 write_flash 0x0 router.bin
```

> 📝 **Note:** The Arduino source code (`router.ino`) is **not yet publicly available**. Only the pre-compiled `router.bin` is currently distributed. The full source will be released in a future update. To be notified, ⭐ star this repo and watch for releases.

---

---

## 🔌 Finding Your COM Port (Windows / Mac / Linux)

When you click **Connect** in the Web Installer, a browser dialog will ask you to select a serial port. Here's how to find the correct one on every operating system.

---

### 🧰 First — Install the USB Driver

> The D1 Mini uses a **CH340** or **CP2102** USB-to-serial chip. If your port doesn't appear, install the driver first.

| Chip | How to identify | Driver Download |
|---|---|---|
| **CH340** | Seen on most cheap D1 Mini clones | [CH340 Driver](https://www.wch-ic.com/downloads/CH341SER_EXE.html) |
| **CP2102** | Seen on some branded D1 Minis | [CP2102 Driver](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) |

> After installing, **unplug and replug** your D1 Mini.

---

### 🪹 Windows

**Method 1 — Device Manager (Most Reliable)**

1. Plug your D1 Mini into your PC via USB
2. Press **`Win + X`** → click **Device Manager**
3. Expand **Ports (COM & LPT)**
4. Look for one of these entries:
   - `USB-SERIAL CH340 (COM3)` → your port is **COM3**
   - `Silicon Labs CP210x (COM4)` → your port is **COM4**
   - The number after COM varies — use whatever number appears
5. That `COMx` value is what you select in the Web Installer

> ⚠️ If nothing appears under **Ports (COM & LPT)**, install the CH340 or CP2102 driver above and retry.

**Method 2 — Quick Check via PowerShell**

```powershell
[System.IO.Ports.SerialPort]::getportnames()
```
Run this in PowerShell. It lists all available COM ports. Plug/unplug the D1 Mini to see which one appears/disappears.

---

### 🍏 macOS

**Method 1 — Terminal (Fastest)**

```bash
ls /dev/cu.*
```

Look for one of these in the output:
- `/dev/cu.usbserial-XXXX` → CH340 chip
- `/dev/cu.SLAB_USBtoUART` → CP2102 chip
- `/dev/cu.wchusbserial1410` → CH340 variant

That full path (e.g. `/dev/cu.usbserial-1410`) is your port. Select it in the Web Installer dialog.

**Method 2 — System Information**

1. Click the **Apple menu ** → **About This Mac** → **System Report**
2. Click **USB** in the left sidebar
3. Look for **CH340**, **CP2102**, or **USB Serial** in the device list

> ⚠️ On **macOS 12+**, the CH340 driver is built-in. On older macOS, download it from the link in the driver table above.

---

### 🐧 Linux

**Method 1 — Terminal (Fastest)**

```bash
ls /dev/ttyUSB*
# or
ls /dev/ttyACM*
```

Look for:
- `/dev/ttyUSB0` → Most common for CH340 and CP2102
- `/dev/ttyACM0` → Some USB serial adapters

Plug/unplug to confirm which one is your D1 Mini:

```bash
dmesg | tail -20
```

Look for a line like:
```
[12345.678] usb 1-1.2: ch341-uart converter now attached to ttyUSB0
```

**Method 2 — Fix Permission Denied Error**

If the Web Installer says **permission denied**, run:

```bash
sudo usermod -a -G dialout $USER
```

Then **log out and log back in**. This adds your user to the `dialout` group which controls serial port access.

---

### 📊 Quick Reference Table

| Operating System | Typical Port Name | Where to Find It |
|---|---|---|
| **Windows** | `COM3`, `COM4`, `COM5`... | Device Manager → Ports (COM & LPT) |
| **macOS** | `/dev/cu.usbserial-XXXX` | Terminal: `ls /dev/cu.*` |
| **Linux** | `/dev/ttyUSB0` | Terminal: `ls /dev/ttyUSB*` |

> 💡 **Tip:** If you have multiple COM ports and are unsure which is the D1 Mini — unplug it, check the list, plug it back in, check again. The new entry is your board.

## ⚙️ Initial Setup & Usage

**Step 1 — Power On**
> Plug in your D1 Mini and wait **15 seconds** for it to boot.

**Step 2 — Connect to Setup Network**
| Setting | Value |
|---|---|
| Network Name | `D1Mini-Setup` |
| Password | *(none — open network)* |

**Step 3 — Open Dashboard**
> Navigate to **http://192.168.4.1** in your browser

**Step 4 — Login**
| Field | Default Value |
|---|---|
| Username | `admin` |
| Password | `admin` |

**Step 5 — Configure**
- Enter your hotel/airport Wi-Fi details in **Upstream**
- Set a strong password for your **Local Hotspot**
- Change your **Admin Password**
- Click **Save and Reboot**

**Step 6 — Reconnect**
> Connect all your devices to your new secured hotspot. Done! ✅

---

## 🛑 Captive Portal Troubleshooting

> **Problem:** Hotel login screen won't appear after connecting through the router.

1. Open the dashboard at **192.168.4.1**
2. Click **Pause DNS**
3. Disconnect and reconnect your phone to the D1 Mini Wi-Fi (flushes DNS cache)
4. Open **http://neverssl.com** in your browser — this forces the hotel portal to trigger
5. Log in to the hotel Wi-Fi
6. Return to dashboard and click **Resume DNS**

> ⚠️ **Note:** If your phone uses **Android Private DNS** or **iCloud Private Relay**, disable it temporarily before step 3.

---

## 📊 Performance

| Metric | Value |
|---|---|
| Max Throughput | ~5–8 Mbps |
| CPU Clock | 160 MHz |
| NAT Engine | LwIP NAPT (v2 Higher Bandwidth) |
| Flash Storage | 4MB (1MB LittleFS) |
| Dashboard | Async, no page reload |

> The ESP8266 is a single-core MCU acting as a software router. 5–8 Mbps is sufficient for browsing, email, VoIP calls, and SD video streaming. It is not designed for 4K streaming or large downloads.

---

## 🏆 Credits

| Contributor | Role |
|---|---|
| **Manojkumar Chandubhai Prajapati** | Project Architect & Lead Developer |
| **Martin Ger** | Inspiration from `esp32_nat_router` project |
| **Google Gemini** | AI pair-programming assistance |

---

## ⚠️ Disclaimer & No Liability

> **READ CAREFULLY BEFORE USING THIS FIRMWARE.**

This project is open-source software distributed under the **MIT License**. By downloading, flashing, or using this firmware in any way, you agree to the following terms in full:

### 🔴 No Liability — Absolute & Universal

**Manojkumar Chandubhai Prajapati** (the author) and any contributors to this project are **NOT liable**, under **any circumstances**, in **any jurisdiction worldwide**, for:

| Category | Examples |
|---|---|
| **Hardware damage** | Bricked D1 Mini, burnt components, failed flash, power surges |
| **Data loss** | Loss of saved configurations, credentials, or any stored data |
| **Network misuse** | Violations of hotel, airport, or public Wi-Fi terms of service |
| **Security incidents** | Unauthorised access, interception, or data breaches |
| **Legal consequences** | Any local, national, or international law violations by the user |
| **Financial loss** | Any direct, indirect, incidental, or consequential damages |
| **Personal injury** | Any physical harm resulting from hardware use or malfunction |
| **Service interruption** | Loss of internet access, network instability, or device failure |

### 📌 Use At Your Own Risk

- This firmware is provided **"AS IS"**, without warranty of any kind, express or implied.
- There is **no guarantee** of fitness for a particular purpose, merchantability, or non-infringement.
- The author makes **no representations** about the suitability of this software for any use.
- It is the **user's sole responsibility** to ensure compliance with all applicable laws and regulations in their country or region.
- It is the **user's sole responsibility** to ensure the hardware is operated safely and within its rated specifications.

### 🌍 Jurisdiction

This disclaimer applies globally, without limitation, regardless of the user's country of residence or the jurisdiction in which this software is used. No local, national, or international law supersedes or modifies the liability exclusions stated above as they pertain to open-source software distributed under the MIT License.

### 🔁 Acknowledgement

By using this firmware, you explicitly acknowledge that:
1. You have read and understood this disclaimer.
2. You accept all risks associated with flashing and operating this firmware.
3. You will not hold the author liable for any outcome resulting from its use.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ for travelers everywhere

⭐ **Star this repo if it helped you!** ⭐

</div>
