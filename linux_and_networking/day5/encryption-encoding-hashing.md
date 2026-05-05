## Encoding

Transforms data into a different format for compatibility (storage/transmission).
Reversible WITHOUT a key.

Purpose is Representation, not security

### Encoding Types 
1. Base64
2. URL Encoding
3. ASCII / UTF-8
5. Hex encoding


## Encryption
Transforms data using a key so that only authorized parties can reverse it.

Purpose is Confidentiality (security)

### Encryption Types
1. Symmetric Encryption
Same key for encryption and decryption

Algorithms:
AES (most common)
DES (obsolete)
3DES (legacy)
ChaCha20


2. Asymmetric Encryption
Two keys: Public + Private

Algorithms:
RSA
ECC (Elliptic Curve)
DSA

## Hashing
Transforms data into a fixed-length output (digest). One-way (cannot be reversed).

Purpose is Integrity, verification, password storage

### Hashing Algorithms
1. Secure (Modern)
2. SHA-256 (widely used)
3. SHA-512
4. SHA-3
5. Bcrypt (for passwords)
6. Argon2 (recommended for passwords)
7. md5 (weak and decrypted)
8. SHA-1 (weak and decrypted)

## Comparision
| Feature       | Encoding      | Encryption        | Hashing            |
| ------------- | ------------- | ----------------  | ------------------ |
| Goal          | Format change | Secure data       | Data integrity     |
| Reversible    | Yes           | Yes (with key)    | No                 |
| Key Required  | No            | Yes               | No                 |
| Output Length | Varies        | Varies            | Fixed              |
| Security      | None          | High              | Depends on algo    |
| Example       | Base64        | AES               | SHA-256            |
