## 🔓 John the Ripper Basics

### General Syntax

```
john [options] [file]
```

- `john` starts the program
- `[options]` define cracking mode or behavior
- `[file]` contains the hash to crack

If the file is in the current directory, only the filename is required.

---

## ⚡ Automatic Hash Cracking

Use this when the hash type is unknown.

```
john --wordlist=[wordlist_path] [hash_file]
```

Example:

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

---

## 🔍 Identifying Hash Types

Online tools:

- [https://hashes.com/en/tools/hash_identifier](https://hashes.com/en/tools/hash_identifier)

Local tool:

- [https://gitlab.com/kalilinux/packages/hash-identifier](https://gitlab.com/kalilinux/packages/hash-identifier)

### Using hash-identifier

1. Download the script
2. Run:

```
python3 hash-id.py
```

3. Paste the hash to get probable formats

---

## 🎯 Cracking with Known Hash Format

```
john --format=[format] --wordlist=[wordlist] [hash_file]
```

Example:

```
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

### Listing Supported Formats

```
john --list=formats
```

Filter formats:

```
john --list=formats | grep -i md5
```

### Format Note

Standard hashes often require the `raw-` prefix.
Example:

- `md5` becomes `raw-md5`
- `sha256` becomes `raw-sha256`

---

## 🪟 Windows Hashes

### NTLM / NTHash

- Used by modern Windows systems
- Stored in:

  - SAM database
  - NTDS.dit in Active Directory

Common extraction tools:

- Mimikatz
- secretsdump

---

## 🐧 Linux Password Hashes

### Combining passwd and shadow

```
unshadow passwd shadow > unshadowed.txt
```

Then crack:

```
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

If needed:

```
john --format=sha512crypt --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

---

## 🧠 Single Crack Mode

Uses usernames and metadata for smarter guesses.

```
john --single --format=[format] [hash_file]
```

Example:

```
john --single --format=raw-sha256 hashes.txt
```

---

## 🛠 Custom Rules

Rules are stored in:

```
/etc/john/john.conf
```

Documentation:
[https://www.openwall.com/john/doc/RULES.shtml](https://www.openwall.com/john/doc/RULES.shtml)

### Using a Rule

```
john --wordlist=[wordlist] --rule=PoloPassword [hash_file]
```

---

## 📦 Cracking Protected Files

### ZIP Files

```
zip2john zipfile.zip > zip_hash.txt
john zip_hash.txt
```

---

### RAR Files

```
rar2john rarfile.rar > rar_hash.txt
john rar_hash.txt
```

Kali path example:

```
/opt/john/rar2john rarfile.rar > rar_hash.txt
```

---

### SSH Private Keys

Convert SSH private key to hash:

```
ssh2john id_rsa > id_rsa_hash.txt
```

If not installed:

```
python3 /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

Then crack:

```
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
```

---

## ✅ Key Takeaways

- Always identify the hash first
- Use `raw-` prefix when needed
- Unshadow Linux hashes before cracking
- File cracking always requires conversion
- Single mode is powerful for user based hashes
