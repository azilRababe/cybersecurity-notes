## IDS Explained Simply

**IDS = Intrusion Detection System**
It **detects attacks** but does **not block them**. It alerts humans or systems.

---

## IDS Deployment Types

### 1. HIDS (Host IDS)

**Think: Bodyguard for one machine**

- Installed on **each host**
- Monitors logs, files, processes
- Very detailed visibility
- Hard to manage at scale
- Uses host resources

**Memory trick**
HIDS = Host = One machine

---

### 2. NIDS (Network IDS)

**Think: Security camera for the whole network**

- Monitors **network traffic**
- Covers all hosts at once
- Centralized detection
- Less detail per host

**Memory trick**
NIDS = Network = All machines

---

## IDS Detection Methods

### 1. Signature Based IDS

**Think: Antivirus rules**

- Matches traffic against known attack patterns
- Fast and accurate for known attacks
- Cannot detect zero day attacks

**Pros**

- Low false positives
- Reliable for known threats

**Cons**

- Blind to new attacks

**Memory trick**
Signature = Known attack

---

### 2. Anomaly Based IDS

**Think: Something feels off**

- Learns normal behavior first
- Alerts on deviation from baseline
- Can detect zero day attacks
- High false positives

**Pros**

- Detects unknown attacks

**Cons**

- Needs tuning
- Flags weird but legit behavior

**Memory trick**
Anomaly = Unusual behavior

---

### 3. Hybrid IDS

**Think: Best of both worlds**

- Uses signatures for known attacks
- Uses anomaly detection for new ones

**Memory trick**
Hybrid = Signature + Anomaly

---

## Snort Overview

- Open source IDS
- Created in 1998
- Supports signature and anomaly detection
- Rule based
- Extremely popular

Snort can:

- Detect known attacks
- Detect custom traffic
- Analyze live traffic
- Analyze PCAP files

---

## Snort Modes Explained

### 1. Packet Sniffer Mode

**Just watching**

- Displays packets
- No detection
- Used for troubleshooting

**Use case**
Network performance issues

---

### 2. Packet Logging Mode

**Recording everything**

- Logs traffic to PCAP
- Can be used later
- Ideal for forensics

**Use case**
Post attack investigation

---

### 3. NIDS Mode

**Real IDS mode**

- Applies rules
- Generates alerts
- Real time detection

**Use case**
Active security monitoring

---

## Where Snort Lives

Main directory:

```
/etc/snort
```

Important file:

```
snort.conf
```

This file defines:

- Networks to monitor
- Rule files to load
- Variables like HOME_NET

---

## Snort Rule Structure Made Easy

Example rule idea:
Detect ICMP ping to loopback

### Rule Parts

- **Action** what to do
  alert
- **Protocol** icmp
- **Source IP** any
- **Source Port** any
- **Destination IP** HOME_NET or specific IP
- **Destination Port** any

---

### Rule Metadata

Inside parentheses

- **msg** alert message
- **sid** unique rule ID
- **rev** revision number

**Memory trick**
msg = message
sid = rule ID
rev = version

---

## Rule Creation Flow

1. Open custom rules file

```
/etc/snort/rules/local.rules
```

2. Add rule

```
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)
```

3. Save file

---

## Testing the Rule

### Start Snort

- Monitor loopback interface
- Show alerts in console

### Generate traffic

```
ping 127.0.0.1
```

### Result

Alert appears
Rule works

---

## Reading the Alert Output

Example:

```
Loopback Ping Detected {ICMP} 127.0.0.1 -> 127.0.0.1
```

Meaning:

- ICMP traffic detected
- Source and destination identified
- Rule triggered successfully

---

## Snort with PCAP Files

Snort can analyze **old traffic** stored in PCAP files.

**Use case**

- Forensics
- Incident response
- Root cause analysis

You run Snort against a PCAP and it applies rules as if traffic is live.

---

## One Page Memory Summary

- IDS detects, IPS blocks
- HIDS = one host
- NIDS = whole network
- Signature = known attacks
- Anomaly = unusual behavior
- Hybrid = both
- Snort = open source IDS
- Packet sniffer = view
- Packet logger = record
- NIDS mode = alert
- PCAP = forensic analysis
