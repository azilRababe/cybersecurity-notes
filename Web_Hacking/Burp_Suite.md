## 🧩 What is Burp Suite

Burp Suite is a Java based web application security testing framework. It is widely considered the industry standard for testing web apps, mobile apps, and APIs.

---

## 🧠 Core Burp Suite Modules

### 🔁 Proxy

- Intercepts HTTP and HTTPS requests and responses
- Allows modifying requests before they reach the server
- Can forward, drop, edit, or send traffic to other tools
- Captures traffic even when interception is off
- Supports WebSocket traffic

### 🔄 Repeater

- Manually resend and modify requests
- Ideal for SQL injection, command injection, logic flaws
- Useful for understanding how endpoints behave

### 🎯 Intruder

- Automated request spraying and fuzzing
- Used for brute forcing, parameter fuzzing, and enumeration
- Rate limited in Community edition

### 🔐 Decoder

- Encodes and decodes data such as:

  - URL encoding
  - Base64
  - Hex

- Useful for payload crafting and data inspection

### 🧮 Comparer

- Compares two requests or responses
- Works at byte level or word level
- Great for spotting subtle differences in responses

### 🎲 Sequencer

- Tests randomness of tokens such as session IDs
- Identifies weak or predictable token generation

---

## ⌨️ Useful Keyboard Shortcuts

| Shortcut         | Action    |
| ---------------- | --------- |
| Ctrl + Shift + D | Dashboard |
| Ctrl + Shift + T | Target    |
| Ctrl + Shift + P | Proxy     |
| Ctrl + Shift + I | Intruder  |
| Ctrl + Shift + R | Repeater  |

---

## 🔍 Burp Proxy Explained

### Intercepting Requests

- Requests pause before reaching the server
- Options available:

  - Forward
  - Drop
  - Edit
  - Send to Repeater or Intruder

- Disable interception by clicking **Intercept is on**

### Traffic Control

- Full visibility and manipulation of client server communication
- Essential for discovering logic flaws and auth issues

### Logging and History

- All traffic is logged automatically
- Viewable in:

  - HTTP history
  - WebSockets history

- Requests can be reused and sent to other modules

### WebSocket Support

- Burp captures and logs WebSocket messages
- Useful for real time applications and APIs

---

## 🌐 Browser Configuration

### FoxyProxy

- Used to route browser traffic through Burp
- Common setup:

  - Proxy: 127.0.0.1
  - Port: 8080

- Firefox recommended for Burp usage

---

## ⚠️ Important Warnings

- If interception is enabled, your browser will appear frozen
- Always turn interception off when not actively testing
- Forgetting this is one of the most common beginner mistakes
- Right click any request to access Burp actions

---

## 🐧 Burp Browser Issues on Linux

### Problem

- Burp Browser may fail to start due to sandbox restrictions

### Smart Option

- Create a low privilege user
- Run Burp Suite under that account
- Safest approach

### Easy Option

- Navigate to:

  - Settings → Tools → Burp’s browser
  - Enable **Allow Burp’s browser to run without a sandbox**

- This reduces security and should only be used in labs or training environments

---

## 🧠 Practical Usage Tips

- Proxy for discovery and traffic manipulation
- Repeater for exploitation and validation
- Intruder for automation and fuzzing
- Decoder for payload preparation
- Comparer for response analysis
- Sequencer for session security testing
