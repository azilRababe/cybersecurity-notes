## 🌍 DNS (Domain Name System)

DNS is responsible for translating domain names into IP addresses.

---

## 🧾 Common DNS Record Types

### A Record

- Maps a hostname to an IPv4 address
- Example:

  ```
  example.com → 172.17.2.172
  ```

### AAAA Record

- Maps a hostname to an IPv6 address
- Quad A refers to IPv6
- Not related to battery sizes or AAA security concepts

### CNAME Record

- Maps one domain name to another domain name
- Example:

  ```
  www.example.com → example.com
  ```

### MX Record

- Specifies the mail server responsible for receiving email for a domain

---

## 🔎 DNS and Domain Lookup Tools

- `nslookup`
  Resolves a domain name to an IP address from the command line

- `whois`
  Displays registration details of a domain, including:

  - Owner
  - Email
  - Phone number
  - Address

---

## 🌐 HTTP and HTTPS

- HTTP uses TCP port **80**
- HTTPS uses TCP port **443**
- Alternate ports include **8080** and **8443**

---

## 🧪 Talking HTTP with Telnet

You can manually interact with a web server using Telnet.

Example:

```
telnet 10.64.170.72 80
```

Required HTTP request:

```
GET / HTTP/1.1
Host: anything
```

Notes:

- Some servers may respond without the Host header
- You can request specific files:

  ```
  GET /file.html HTTP/1.1
  ```

- This method is useful for troubleshooting and learning HTTP behavior

---

## 📁 FTP (File Transfer Protocol)

FTP is designed for transferring files between systems.

- Default port: **TCP 21**
- Anonymous login is often supported

### Common FTP Commands

- `USER` → specify username
- `PASS` → specify password
- `RETR` → download a file from the server
- `STOR` → upload a file to the server

---

## ✉️ SMTP (Simple Mail Transfer Protocol)

SMTP defines how email is sent between mail clients and mail servers.

- Default port: **TCP 25**

### Common SMTP Commands

- `HELO` or `EHLO` → starts the SMTP session
- `MAIL FROM:` → sender address
- `RCPT TO:` → recipient address
- `DATA` → begin sending email content
- `.` → ends the message content

---

## 📬 POP3 (Post Office Protocol v3)

POP3 allows a client to retrieve email from a mail server.

- Default port: **TCP 110**
- Messages are typically deleted after retrieval

### Common POP3 Commands

- `USER <username>` → identify user
- `PASS <password>` → authenticate
- `STAT` → message count and size
- `LIST` → list messages
- `RETR <number>` → retrieve a message
- `DELE <number>` → mark message for deletion
- `QUIT` → end session and apply changes

### Simple Analogy

- SMTP is like sending mail at the post office
- POP3 is like checking your home mailbox

---

## 📥 IMAP (Internet Message Access Protocol)

IMAP allows synchronized email access across multiple devices.

- Messages remain on the server
- Supports folders and message state tracking
- Default port: **TCP 143**

### Common IMAP Commands

- `LOGIN <username> <password>` → authenticate
- `SELECT <mailbox>` → choose mailbox
- `FETCH <id> BODY[]` → retrieve message content
- `MOVE <set> <mailbox>` → move messages
- `COPY <set> <mailbox>` → copy messages
- `LOGOUT` → end session

---

## 📊 Default Port Summary

| Protocol | Transport  | Port |
| -------- | ---------- | ---- |
| TELNET   | TCP        | 23   |
| DNS      | UDP or TCP | 53   |
| HTTP     | TCP        | 80   |
| HTTPS    | TCP        | 443  |
| FTP      | TCP        | 21   |
| SMTP     | TCP        | 25   |
| POP3     | TCP        | 110  |
| IMAP     | TCP        | 143  |
