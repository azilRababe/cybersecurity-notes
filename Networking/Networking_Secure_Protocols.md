## 🔐 Transport Layer Security (TLS)

TLS is used to secure existing application protocols by providing:

- **Confidentiality** through encryption
- **Integrity** to prevent data tampering
- **Authenticity** to verify server identity

TLS is added on top of other protocols without changing how they fundamentally work.

---

## 🚫 Insecure Protocols and Default Ports

| Protocol | Default TCP Port |
| -------- | ---------------- |
| HTTP     | 80               |
| SMTP     | 25               |
| POP3     | 110              |
| IMAP     | 143              |

These protocols transmit data in plaintext.

---

## ✅ Secure Versions Using TLS

| Protocol | Default TCP Port |
| -------- | ---------------- |
| HTTPS    | 443              |
| SMTPS    | 465, 587         |
| POP3S    | 995              |
| IMAPS    | 993              |

TLS can be applied to many other protocols, offering the same security benefits.

---

## 🔑 OpenSSH Overview

OpenSSH provides secure remote access and communication over untrusted networks.

### Key Benefits

- **Secure authentication**
  Supports passwords, public key authentication, and two factor authentication

- **Confidentiality**
  Encrypts all traffic end to end and warns about new or changed server keys to reduce man in the middle risks

- **Integrity**
  Ensures data is not modified during transmission

- **Tunneling**
  Allows other protocols to be securely routed through SSH, similar to a VPN

- **X11 Forwarding**
  Enables running graphical applications remotely over the network

---

## 🖥️ X11 Forwarding with SSH

To enable graphical applications over SSH:

```
ssh -X 192.168.124.148
```

Requirements:

- Local system must support a graphical environment
- Remote system must allow X11 forwarding

---

## ⚠️ SFTP vs FTPS

- **SFTP**

  - Runs over SSH
  - Encrypted by default
  - Uses SSH transport

- **FTPS**

  - FTP secured with TLS
  - Usually uses TCP port **990**
  - Different protocol from SFTP

Important note:

- FTP uses port **21**
- FTPS commonly uses port **990**
- SFTP does not use FTP at all
