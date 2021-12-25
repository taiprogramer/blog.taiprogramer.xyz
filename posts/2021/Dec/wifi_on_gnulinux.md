
[//]: <> (SPDX-License-Identifier: CC0-1.0)
[//]: <> (Copyright © 2021 Huynh Van Tai)

# Connect to Wi-Fi on GNU/Linux (terminal)

**Disclaimer:**
The document author has published this document with the hope that it may be
helpful to others. However, the author does not guarantee that all information
contained in this document is correct or accurate. There is no warranty,
expressed or implied, of merchantability or fitness for any purpose. The author
does not assume any liability or responsibility for using the information
contained in this document.

**Date created**: Dec 25 2021

## Why?

- For everyone who wants to become a cool kid.
- For everyone who loves working with a terminal rather than GUI.
- For everyone who needs to feel how extensibility of the GNU/Linux Operating
  System.

## Commands

Make sure you can run all these commands before you get started.

- **rfkill** -  tool for enabling and disabling wireless devices
- **wpa_passphrase** - Generate a WPA PSK from an ASCII passphrase for a SSID
- **wpa_supplicant** - Wi-Fi Protected Access client and IEEE 802.1X supplicant
- **ip** -  show / manipulate routing, network devices, interfaces and tunnels
- **iw** - show / manipulate wireless devices and their configuration
- **dhcpcd** - a DHCP client

## Main

- First, unlock your wifi device if it's locked.

```sh
sudo rfkill unblock wifi
```

- Secondly, turn on your wireless interface. In my case, the wireless interface
  is `wlan0`. Your wireless interface may look different, like `wlp1s0`
  (predictable network interface). But to know what does it look like, type **ip
  a**.

```sh
sudo ip link set wlan0 up
```

- Thirdly, scan for SSID (wifi name) and ask your neighbor what the password is.
  If it's your wifi, go to the next step.

```sh
sudo iw dev wlan0 scan | grep SSID
```

- Fourthly, generate a config file, replace your corresponding SSID & password.
  In my case, SSID is **Huynh Van Tai**, and the password is **hanxinhdep**.

```sh
wpa_passphrase "Huynh Van Tai" "hanxinhdep" > xxx.conf
```

- Fifthly, connect to Wi-Fi using the config file

```sh
sudo wpa_supplicant -c xxx.conf -i wlan0 & disown
```

- Finally, get the IP address & other things with the DHCP client.

```sh
sudo dhcpcd wlan0
```

---

This document is licensed under the Creative Commons Zero v1.0 Universal.

Examples, recipes, and other code in this document are additionally licensed
under the Unlicense.
