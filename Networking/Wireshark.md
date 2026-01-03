## 🦈 Wireshark Basics

Wireshark is an open source, cross platform network packet analyzer. It can capture live network traffic and analyze packet capture files such as PCAP. It is widely considered one of the most powerful tools for packet inspection and network troubleshooting.

---

## 📦 Packet Dissection in Wireshark

Wireshark breaks each packet into multiple logical layers that closely map to the OSI model.

---

### Frame Layer (OSI Layer 1)

- Displays general information about the captured frame
- Includes timing and physical layer details

---

### Source and Destination MAC Addresses (OSI Layer 2)

- Shows source and destination MAC addresses
- Represents the Data Link layer

---

### Source and Destination IP Addresses (OSI Layer 3)

- Displays IPv4 or IPv6 source and destination addresses
- Represents the Network layer

---

### Transport Protocol Details (OSI Layer 4)

- Shows protocol information such as TCP or UDP
- Displays source and destination port numbers
- May include sequence and acknowledgment numbers

---

### Protocol Errors and Reassembly

- Highlights TCP segments that require reassembly
- Displays retransmissions, out of order packets, and errors

---

### Application Protocol (OSI Layer 7)

- Displays application protocols such as HTTP, FTP, DNS, and SMB
- Shows protocol specific headers and commands

---

### Application Data

- Displays the actual payload carried by the application protocol
- May include readable content if the data is not encrypted

---

## 🔍 Wireshark Filtering Types

Wireshark supports two filtering methods.

### Capture Filters

- Applied before packet capture begins
- Only packets matching the filter are captured
- Based on Berkeley Packet Filter syntax

Example:

```
tcp port 80
```

---

### Display Filters

- Applied after packets are captured
- Used to show or hide packets without discarding data
- Uses Wireshark display filter syntax

Example:

```
http
```
