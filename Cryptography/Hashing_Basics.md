## Hashing and Encoding

### Hash Output and Encoding

- Hash functions output raw bytes.
- These bytes are commonly encoded for readability and storage.
- Most common encodings:

  - Hexadecimal
  - Base64

- Linux tools like:

  - md5sum
  - sha1sum
  - sha256sum
  - sha512sum
    output hashes in hexadecimal format.

---

### Hash Cracking and Rainbow Tables

- Sites like CrackStation and Hashes.com use rainbow tables.
- Rainbow tables are large precomputed lists of hashes.
- Lookup in a sorted hash list is much faster than brute forcing.
- Unsalted hashes are extremely vulnerable to this technique.
- Salting effectively breaks rainbow table attacks.

---

### Secure Password Storage Best Practice

1. Choose a strong password hashing algorithm:

   - Argon2 (recommended)
   - Scrypt
   - Bcrypt
   - PBKDF2

2. Generate a unique random salt for each password.
3. Concatenate password + salt.
4. Hash the combined value using the chosen algorithm.
5. Store:

   - The resulting hash
   - The salt
   - The algorithm parameters

Important additions:

- Never reuse salts.
- Never store plaintext passwords.
- Password hashing is intentionally slow to resist brute force attacks.
- Use memory hard algorithms like Argon2 or Scrypt to resist GPU attacks.

---

### Unix and Linux Password Hash Format

Stored as:

```
$prefix$options$salt$hash
```

- Prefix identifies the algorithm.
- Options store parameters like cost or memory usage.
- Salt is unique per password.
- Hash is the final derived value.

#### Common Prefixes

- `$y$` yescrypt (modern default and recommended)
- `$gy$` gost-yescrypt
- `$7$` scrypt
- `$2b$`, `$2y$`, `$2a$`, `$2x$` bcrypt
- `$6$` sha512crypt
- `$md5` SunMD5
- `$1$` md5crypt

Security note:

- MD5 based schemes are considered weak and deprecated.

---

### Windows Password Hashes

- Windows uses NTLM, derived from MD4.
- NTLM hashes look similar to MD4 or MD5.
- Context is required to identify them correctly.
- Password hashes are stored in the SAM database.
- Windows restricts access, but tools like mimikatz can dump hashes.
- Two types of hashes:

  - LM hash (very weak, legacy)
  - NT hash (stronger but still outdated)

---

### Hashcat Basics

Syntax:

```
hashcat -m <hash_type> -a <attack_mode> hashfile wordlist
```

Key concepts:

- `-m` specifies the hash type.
- `-a` specifies the attack mode.
- Common attack modes:

  - 0 straight
  - 1 combination
  - 3 brute force
  - 6 hybrid wordlist + mask
  - 7 hybrid mask + wordlist

---

### HMAC (Keyed Hash)

- Used to verify integrity and authenticity.
- Combines:

  - A cryptographic hash function
  - A secret key

- Protects against length extension attacks.

Formula:

```
HMAC(K, M) = H((K ⊕ opad) || H((K ⊕ ipad) || M))
```

Where:

- K is the secret key
- M is the message
- ipad and opad are fixed constants

Common uses:

- API authentication
- JWT signatures
- Secure message verification

---

### Hashing vs Encryption vs Encoding

#### Hashing

- One way process.
- Produces fixed length output.
- Small input change results in large output change.
- Used for:

  - Password storage
  - Integrity checks

- Cannot be reversed.

#### Encryption

- Two way process.
- Requires a key.
- Can be decrypted.
- Used for:

  - Confidentiality
  - Secure communication

#### Encoding

- Converts data to another format.
- Fully reversible.
- No security provided.
- Used for compatibility and transmission.

---

### Character Encoding Overview

- ASCII
- ISO-8859-1
- Windows-1252
- UTF-8
- UTF-16
- UTF-32

Important notes:

- UTF encodings are Unicode based.
- Unicode supports global languages including Arabic and Japanese.
- UTF-8 is the most widely used encoding today.
- Encoding issues can cause hash mismatches if not handled correctly.

---

### Extra Practical Notes

- Always hash the exact byte representation of data.
- Encoding differences change hash results.
- Never use fast hashes like MD5 or SHA1 for passwords.
- Use constant time comparison when checking hashes.
- Salts do not need to be secret.
- Keys used in HMAC must remain secret.
