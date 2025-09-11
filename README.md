# Flutter Development Setup for Android Phone and Laptop

This guide explains how to connect your Android phone to your laptop for Flutter development, including both USB and wireless debugging methods.

---

## 1. For Phones Without Wireless Debugging

1. 7 taps on MIUI version to enable developer options on additional settings ,
2. Developer options: turn on usb debugging , install via usb if (android 11+) turn on wireless debugging feature
3. for ip: about phone> all specs> status
1. Enable **USB debugging** on your phone. // 
2. Connect your phone to the laptop via USB.
3. Run the following commands:

```bash
# Enable TCP/IP mode on port 5555
adb tcpip 5555

# Connect to the device via Wi-Fi
adb connect 192.168.18.48:5555

# Verify connected devices
adb devices
Example output:

nginx
Copy code
List of devices attached
AINR6PUOGMDIJRHU	device
192.168.18.48:5555	device
Run flutter devices to check if Flutter detects your phone.

Optional: Disconnect when done

bash
Copy code
adb disconnect 192.168.18.48:5555
2. For Phones With Wireless Debugging Feature
On your phone, enable Wireless Debugging in Developer Options.

Note the IP address + port and the pairing code displayed on your phone.

On your laptop, run:

bash
Copy code
adb pair <IP_ADDRESS>:<PAIRING_PORT>
Example:

bash
Copy code
adb pair 192.168.1.105:43127
After pairing, connect to your phone:

bash
Copy code
adb connect <IP_ADDRESS>:5555
Run flutter devices to verify the connection.

Optional: Disconnect when done

bash
Copy code
adb disconnect <IP_ADDRESS>:5555
3. Tips for Next Time
Check your phone's current IP address:
Settings → About Phone → Status → IP address

Replace the old IP with the new one in adb connect NEW_IP:5555.

yaml
Copy code

---

### **setup.txt**  

Flutter Development Setup - Phone and Laptop

Phones Without Wireless Debugging:

Enable USB debugging on your phone

Connect phone via USB

Commands:
adb tcpip 5555
adb connect 192.168.18.48:5555
adb devices

Check Flutter:
flutter devices

Disconnect:
adb disconnect 192.168.18.48:5555

Phones With Wireless Debugging:

Enable Wireless Debugging on phone

Note IP + port and pairing code

Pair:
adb pair 192.168.1.105:43127

Connect:
adb connect 192.168.1.105:5555

Check Flutter:
flutter devices

Disconnect:
adb disconnect 192.168.1.105:5555