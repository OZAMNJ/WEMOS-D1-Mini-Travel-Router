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

---

### Option B — Manual Flash with esptool

```bash
# Install esptool
pip install esptool

# Flash the firmware (replace COM3 with your port)
esptool.py --port COM3 --baud 460800 write_flash 0x0 router.bin
```

---

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

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ for travelers everywhere

⭐ **Star this repo if it helped you!** ⭐

</div>
