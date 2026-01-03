## 🐧 tcpdump Basics

`tcpdump` is a powerful command line packet analyzer used to capture and inspect network traffic in real time or from saved capture files.

---

## 🌐 Network Interfaces

- `ip address show` or `ip a s`
  Lists all available network interfaces.

- `-i any`
  Capture traffic on all available interfaces.

- `-i <interface>`
  Capture traffic on a specific interface.
  Example:

  ```
  tcpdump -i eth0
  ```

---

## 💾 Capture and Read Files

- `-w FILE`
  Save captured packets to a file, usually with a `.pcap` extension.

- `-r FILE`
  Read packets from an existing capture file.

- `-c COUNT`
  Capture only a specific number of packets.

---

## 🧾 Name Resolution Options

- `-n`
  Do not resolve IP addresses to hostnames.

- `-nn`
  Do not resolve IP addresses or port numbers.

---

## 🔍 Verbosity Levels

- `-v`
  Verbose output.

- `-vv`
  More verbose output.

- `-vvv`
  Maximum verbosity.
  Refer to the manual page for details.

---

## 📌 Common tcpdump Options Summary

| Command                | Explanation                          |
| ---------------------- | ------------------------------------ |
| `tcpdump -i INTERFACE` | Capture on a specific interface      |
| `tcpdump -w FILE`      | Write packets to file                |
| `tcpdump -r FILE`      | Read packets from file               |
| `tcpdump -c COUNT`     | Capture limited number of packets    |
| `tcpdump -n`           | Disable DNS resolution               |
| `tcpdump -nn`          | Disable DNS and port name resolution |
| `tcpdump -v`           | Verbose output                       |

---

## 🎯 Host and Port Filters

- `host <IP>` or `host <HOSTNAME>`
  Capture packets related to a specific host.

- `src host <IP>`
  Capture packets from a specific source host.

- `dst host <IP>`
  Capture packets sent to a specific destination host.

- `port <PORT>`
  Capture traffic on a specific port.
  Example:

  ```
  tcpdump port 53
  ```

- `src port <PORT>`
  Filter by source port.

- `dst port <PORT>`
  Filter by destination port.

---

## 🧠 Logical Operators

- `and`
  Both conditions must be true.
  Example:

  ```
  tcpdump host 1.1.1.1 and tcp
  ```

- `or`
  Either condition can be true.
  Example:

  ```
  tcpdump udp or icmp
  ```

- `not`
  Exclude matching traffic.
  Example:

  ```
  tcpdump not tcp
  ```

---

## 📊 Protocol Filters

- `tcpdump ip`
- `tcpdump ip6`
- `tcpdump icmp`
- `tcpdump arp`

Filters packets by protocol type.

---

## 📏 Packet Size Filters

- `greater LENGTH`
  Capture packets larger than or equal to a specific size.

- `less LENGTH`
  Capture packets smaller than or equal to a specific size.

---

## 🔬 Advanced Byte Level Filtering

tcpdump allows filtering specific bytes using this syntax:

```
proto[expr:size]
```

- `proto` → protocol such as ether, ip, ip6, tcp, udp, icmp, arp
- `expr` → byte offset starting at 0
- `size` → number of bytes to inspect, optional, defaults to 1

This is useful for advanced analysis and protocol inspection.

---

## 🧪 Output Formatting Options

- `-q`
  Quick output with minimal packet information.

- `-e`
  Display link layer headers including MAC addresses.

- `-A`
  Display packet data in ASCII.

- `-xx`
  Display packet data in hexadecimal format.

- `-X`
  Display packet data in both hexadecimal and ASCII.

---

## 📋 Output Options Summary

| Command       | Explanation           |
| ------------- | --------------------- |
| `tcpdump -q`  | Brief output          |
| `tcpdump -e`  | Show MAC addresses    |
| `tcpdump -A`  | ASCII output          |
| `tcpdump -xx` | Hexadecimal output    |
| `tcpdump -X`  | Hexadecimal and ASCII |
