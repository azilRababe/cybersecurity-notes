## 🧭 What is Gobuster

Gobuster is an open source enumeration tool written in Go. It brute forces and discovers:

- Web directories and files
- DNS subdomains
- Virtual hosts
- Amazon S3 buckets
- Google Cloud Storage buckets

It works by sending requests built from wordlists and analyzing server responses.

---

## 🧠 Core Concepts

### Enumeration

Enumeration means listing all possible resources, whether accessible or not.
Example: finding hidden directories like `/admin`, `/uploads`, `/backup`.

### Brute Force

Brute force means trying every possible option from a wordlist until a match is found.
Gobuster uses this technique for directories, subdomains, and vhosts.

---

## 📂 Directory Enumeration Mode (dir)

### Basic Syntax

```
gobuster dir -u <url> -w <wordlist>
```

### Example

```
gobuster dir -u http://example.thm/ -w /usr/share/wordlists/dirb/small.txt -t 64
```

### Explanation

- `dir` enables directory and file enumeration
- `-u` specifies the target URL
- `-w` specifies the wordlist
- `-t` sets the number of threads

---

## ⚙️ Common Directory Mode Flags

| Short   | Long                     | Description                         |
| ------- | ------------------------ | ----------------------------------- |
| -t      | --threads                | Number of concurrent threads        |
| -w      | --wordlist               | Wordlist used for enumeration       |
| -o      | --output                 | Save output to file                 |
| --delay |                          | Delay between requests              |
| --debug |                          | Debug unexpected errors             |
| -x      | --extensions             | File extensions to check (.php,.js) |
| -c      | --cookies                | Send cookies with requests          |
| -H      | --headers                | Send custom headers                 |
| -k      | --no-tls-validation      | Ignore TLS certificate errors       |
| -n      | --no-status              | Hide HTTP status codes              |
| -s      | --status-codes           | Show only specific status codes     |
| -b      | --status-codes-blacklist | Hide specific status codes          |
| -r      | --follow-redirect        | Follow HTTP redirects               |
| -U      | --username               | Authenticated requests              |
| -P      | --password               | Password for authentication         |

---

## 🌐 DNS Subdomain Enumeration Mode (dns)

### Purpose

Used to brute force DNS subdomains like:

```
admin.example.thm
blog.example.thm
dev.example.thm
```

### Syntax

```
gobuster dns -d <domain> -w <wordlist>
```

### Example

```
gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

### Required Flags

- `dns` enables DNS mode
- `-d` specifies the domain
- `-w` specifies the subdomain wordlist

### Useful DNS Flags

| Flag         | Description                |
| ------------ | -------------------------- |
| -i           | Show resolved IP addresses |
| --show-cname | Show CNAME records         |
| -r           | Use custom DNS resolver    |
| -d           | Domain to enumerate        |

---

## 🖥️ Virtual Host Enumeration Mode (vhost)

### What is a Virtual Host

Virtual hosts are multiple websites hosted on the same IP.
They are not DNS based like subdomains.

### Difference Between dns and vhost

- dns mode performs DNS lookups
- vhost mode sends HTTP requests with different Host headers

---

### Syntax

```
gobuster vhost -u <url> -w <wordlist> --append-domain
```

### Example

```
gobuster vhost -u http://example.thm -w common.txt --append-domain --exclude-length 279
```

### Important Flags

| Flag             | Description                        |
| ---------------- | ---------------------------------- |
| -u               | Base URL                           |
| --append-domain  | Appends domain to wordlist entries |
| -m               | HTTP method                        |
| --exclude-length | Filter false positives             |
| -r               | Follow redirects                   |

---

## 🚨 False Positives and Filtering

Some servers return identical 404 pages for invalid hosts or paths.
These usually have similar response sizes.

### Solution

Use:

```
--exclude-length <size>
```

Example false positive:

```
Found: test.example.thm Status: 404 [Size: 279]
```

Filtering by size removes most noise.

---

## 🧠 Best Practices

- Start with small wordlists
- Increase threads gradually
- Watch for rate limiting
- Always filter false positives
- Combine Gobuster with Burp or browser testing

---

## 🎯 When to Use Gobuster

- Web application recon
- Hidden directory discovery
- Subdomain enumeration
- Virtual host discovery
- CTF challenges
- Authorized pentests
