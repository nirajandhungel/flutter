# 📱 Flutter Development: Android Phone Setup Guide

<div align="center">

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

A comprehensive guide for connecting your Android device to your development machine for Flutter development.
</div>

## 📋 Prerequisites

Before starting, ensure you have:

- Flutter SDK installed and configured
- Android Studio with Android SDK
- USB drivers for your Android device
- Both devices connected to the same Wi-Fi network (for wireless debugging)

## 🚀 Setup Guide

### 1. Enable Developer Options

1. Go to `Settings` → `About Phone`
2. Tap `Build Number` 7 times until you see "You are now a developer!"
3. Navigate to `Settings` → `System` → `Developer Options`
4. Toggle ON `Developer Options`

### 2. Connection Methods

<details>
<summary><b>Method 1: USB Debugging (All Android Devices)</b></summary>

#### Step 1: Enable USB Debugging
1. Enable Developer Options (as shown above)
2. Turn on `USB debugging`
3. For Android 11+: Enable `Install via USB` and `Wireless debugging`

#### Step 2: Connect via USB
```bash
# Enable TCP/IP mode on port 5555
adb tcpip 5555

# Find your phone's IP address
# Settings → About Phone → Status → IP address
# Or run:
adb shell ip route

# Connect to your device via Wi-Fi
adb connect <PHONE_IP_ADDRESS>:5555

# Example:
adb connect 192.168.18.48:5555

# Verify connected devices
adb devices
```

#### Step 3: Verify Flutter Connection
```bash
flutter devices
```

Expected output:
```
List of devices attached
<device_id>    device
<PHONE_IP_ADDRESS>:5555    device
```

#### Step 4: Disconnect
```bash
adb disconnect <PHONE_IP_ADDRESS>:5555
```
</details>

<details>
<summary><b>Method 2: Wireless Debugging (Android 11+)</b></summary>

#### Step 1: Enable Wireless Debugging
1. Enable Developer Options
2. Turn on `Wireless debugging`
3. Note the IP address, port, and pairing code displayed on your phone

#### Step 2: Pair and Connect
```bash
# Pair with your device
adb pair <IP_ADDRESS>:<PAIRING_PORT>

# Example:
adb pair 192.168.1.105:43127

# Connect to your device
adb connect <IP_ADDRESS>:<DEBUG_PORT>

# Example:
adb connect 192.168.1.105:5555
```

#### Step 3: Verify Connection
```bash
adb devices
flutter devices
```

#### Step 4: Disconnect
```bash
adb disconnect <IP_ADDRESS>:5555
```
</details>

## 🔍 Troubleshooting

| Issue | Solution |
|-------|----------|
| Device not showing in `adb devices` | - Check USB debugging is enabled<br>- Try different USB cable/port<br>- Restart ADB server: `adb kill-server && adb start-server` |
| Connection refused errors | - Ensure both devices are on same Wi-Fi<br>- Check firewall settings |
| Wireless debugging not working | - Verify Android 11+ on device<br>- Restart wireless debugging |
| IP address changes frequently | - Set static IP on router<br>- Check IP before connecting |

### 🔎 Finding Your Phone's IP Address

- **Method 1:** `Settings` → `About Phone` → `Status` → `IP address`
- **Method 2:** Connect via USB and run: `adb shell ip route`
- **Method 3:** `Settings` → `Wi-Fi` → Tap connected network → View IP address

## 💡 Pro Tips

- Create aliases or scripts to automate the connection process
- Default ADB port is 5555 for wireless connections
- Only enable wireless debugging on trusted networks
- Keep USB cable handy as backup

## 📝 Important Notes

- Wireless debugging requires Android 11 or higher
- USB connection is recommended for initial setup
- Settings may vary by manufacturer (MIUI, OxygenOS, etc.)
- Always disconnect properly to avoid future connection issues

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">
⭐ Found this helpful? Star this repository!
</div>