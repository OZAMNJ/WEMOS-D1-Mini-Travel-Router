🌐 D1 Mini Travel Router (Ultimate Edition)
A lightweight, high-performance NAT travel router designed specifically for the ESP8266 (Wemos D1 Mini).

This firmware transforms a standard, low-cost D1 Mini into a secure hardware travel router. It allows you to bypass restrictive hotel/airport captive portals, hide multiple personal devices behind a single MAC address, and enforce custom DNS blocking (like Control D or NextDNS) at the network level.

✨ Key Features
True Hardware NAT: Leverages the LwIP NAPT implementation to securely route traffic between public upstream networks and your private local devices.

Captive Portal Bypass Mode: Engineered with a specific "Pause DNS" toggle that temporarily disables custom DNS routing, allowing seamless logins to public Wi-Fi portal pages.

Persistent LittleFS Storage: Built with a robust file system to securely save your custom configurations, SSIDs, and admin passwords across reboots and power cycles without memory corruption.

Custom DNS Injection: Instantly route all connected devices through a custom DNS provider to block ads, trackers, and malware at the router level.

Modern Web Dashboard: A responsive, dark-mode, asynchronous web UI accessible at 192.168.4.1 that updates metrics in real-time without page reloads.

160MHz Hardware Optimization: Tuned to run at double the standard ESP8266 clock speed, maximizing software NAT throughput and dashboard responsiveness.

🛠️ Hardware Requirements
Wemos D1 Mini (ESP8266EX microcontroller)

Micro-USB or USB-C Data Cable

A USB power bank or wall adapter for travel use.

🚀 Installation Guide
There are two ways to install this firmware onto your D1 Mini.

Option A: One-Click Web Installer (Recommended)
You can flash this firmware directly to your D1 Mini right from your browser using ESP Web Tools.
(Note: This requires a WebSerial compatible browser like Google Chrome or Microsoft Edge).

Plug your D1 Mini into your computer.

Go to the Web Installer page: https://ozamnj.github.io/WEMOS-D1-Mini-Travel-Router

Click Connect, select your USB COM port (you can find from device manager in your pc for your Board from com port section, and click Install.

Option B: Manual Compilation (Arduino IDE)
If you prefer to compile the source code yourself to make further modifications:

Download the router.ino file from the source folder.

Open the file in the Arduino IDE.

You MUST select the following board parameters for the router to function:

Board: LOLIN(WEMOS) D1 R2 & mini

CPU Frequency: 160 MHz (Required for performance)

lwIP Variant: v2 Higher Bandwidth (CRITICAL: NAT will fail without this)

Flash Size: 4MB (FS: 1MB OTA:~1019KB) (Required for LittleFS saving)

Compile and upload to your board.

⚙️ Initial Setup & Usage
Power On: Plug in your flashed D1 Mini. Wait 15 seconds.

Connect: Open your phone or laptop and connect to the default setup network:

Network Name: D1Mini-Setup

Password: (Leave blank / Open network)

Open Dashboard: Open a web browser and navigate to exactly http://192.168.4.1

Login: Enter the default admin credentials:

Username: admin

Password: admin

Configure: * Enter the hotel/airport Wi-Fi details in the Upstream section.

Create a secure password for your Local Hotspot.

Change the Admin Login Password.

Click Save and Reboot.

Final Step: Reconnect your phone/laptop to your newly secured hotspot name.

🛑 Troubleshooting Captive Portals (Hotel/Airport Wi-Fi)
If you are at a hotel and the login screen won't pop up:

Open the D1 Mini Dashboard at 192.168.4.1.

Click Pause DNS.

Disconnect your phone from the D1 Mini Wi-Fi, then reconnect to it (this forces your phone to drop the cached DNS).

Open a browser and type http://neverssl.com. This will force the hotel's login page to trigger.

Once you are logged into the hotel Wi-Fi, go back to the dashboard and click Resume DNS.

Note: If your phone uses "Private DNS" (Android) or "iCloud Private Relay" (Apple), you must temporarily disable it to trigger captive portals.

📊 Performance Expectations
The ESP8266 is a highly capable microcontroller, but it is acting as a software router. Because it features a single-core processor, maximum download speeds through the NAT bridge will physically cap around 5 to 8 Mbps.

This is more than enough bandwidth for browsing the web, checking emails, making VoIP calls, and streaming standard-definition video while traveling, but it is not designed for heavy 4K downloads.

🏆 Credits and Acknowledgments
Manojkumar Chandubhai Prajapati: Project Architect and Lead Developer.

Martin Ger: For the foundational networking inspiration drawn from the esp32_nat_router repository, which demonstrated the immense potential of microcontroller-based NAT routing.

Google Gemini: For serving as an AI pair-programmer in optimizing the LwIP network stack, resolving memory persistence via LittleFS, and designing the asynchronous web dashboard.
