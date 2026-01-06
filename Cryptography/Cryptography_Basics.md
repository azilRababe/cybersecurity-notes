## 🔐 Cryptography Fundamentals

### Plaintext

Plaintext is the original, readable data before encryption.
It can be text, documents, images, multimedia files, or any binary data.

---

### Ciphertext

Ciphertext is the encrypted, unreadable output after encryption.
Ideally, no information about the original plaintext can be derived from it, except approximate size.

---

### Cipher

A cipher is a mathematical algorithm used to transform plaintext into ciphertext and back again.
Ciphers are public knowledge and rely on secret keys for security.

---

### Key

A key is a string of bits used by a cipher to encrypt or decrypt data.

- The cipher is public
- The key must remain secret
- Exception: public keys in asymmetric encryption

---

### Encryption

Encryption converts plaintext into ciphertext using:

- a cipher
- a key

---

### Decryption

Decryption converts ciphertext back into plaintext using:

- the same cipher
- the correct key

Without the key, recovering the plaintext should be computationally infeasible.

---

## 🔑 RSA Concepts for CTFs

### Important RSA Variables

- `p` and `q`
  Large prime numbers

- `n = p × q`
  Modulus

- Public key
  `(n, e)`

- Private key
  `(n, d)`

- `m`
  Plaintext message

- `c`
  Ciphertext

---

### Useful RSA CTF Tools

- RsaCtfTool
  [https://github.com/RsaCtfTool/RsaCtfTool](https://github.com/RsaCtfTool/RsaCtfTool)

- rsatool
  [https://github.com/ius/rsatool](https://github.com/ius/rsatool)

- Practice room
  [https://tryhackme.com/room/breakrsa](https://tryhackme.com/room/breakrsa)

---

## 🔐 SSH Key Algorithms

`ssh-keygen` is commonly used to generate SSH key pairs.

Supported algorithms include:

### DSA

Digital Signature Algorithm
Designed specifically for digital signatures

---

### ECDSA

Elliptic Curve Digital Signature Algorithm
Provides equivalent security with smaller key sizes

---

### ECDSA-SK

ECDSA with Security Key
Uses hardware security keys to protect private keys

---

### Ed25519

Uses EdDSA with Curve25519
Fast, secure, and widely recommended

---

### Ed25519-SK

Ed25519 with Security Key
Uses hardware backed key protection

---

## 🔑 SSH Key Usage

- Specify a private key when connecting:

```
ssh -i privateKeyFileName user@host
```

- Default SSH key directory:

```
~/.ssh/
```

- `authorized_keys`
  Contains public keys allowed to access the server

---

## 🔐 PGP and GPG

### PGP

Pretty Good Privacy
Used for file encryption, email security, and digital signatures

---

### GPG

GNU Privacy Guard
Open source implementation of the OpenPGP standard

Common uses:

- Encrypt email messages
- Sign messages to ensure integrity
- Verify sender identity

---

### GPG Commands

- Import a key:

```
gpg --import backup.key
```

- Decrypt a file:

```
gpg --decrypt confidential_message.gpg
```

---

## 🧠 Security Terminology

### Cryptography

The science of securing communication and data using codes and ciphers.

---

### Cryptanalysis

The study of breaking cryptographic systems without knowing the key.

---

### Brute Force Attack

An attack that tries every possible key or password until the correct one is found.

---

### Dictionary Attack

An attack that tries words or combinations from predefined wordlists.
