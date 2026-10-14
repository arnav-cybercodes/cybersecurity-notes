# Cryptography Fundamentals for Cybersecurity

## 1. What Is Cryptography?

Cryptography is the science of protecting information using mathematical techniques. It helps secure data during storage, transmission, authentication, and communication.

Cryptography is widely used in cybersecurity to protect sensitive information, verify data integrity, authenticate users and systems, and establish secure communication channels.

### Applications of Cryptography

- Secure web browsing using HTTPS.
- Protecting passwords and authentication credentials.
- Encrypting files, disks, and backups.
- Verifying software downloads and digital evidence.
- Authenticating users, servers, and messages.
- Protecting communications between systems.
- Detecting unauthorized modifications to data.

## 2. The CIA Triad

The CIA triad is a fundamental information security model.

| Principle | Meaning | Example |
|---|---|---|
| Confidentiality | Preventing unauthorized access to information | Encrypting sensitive files |
| Integrity | Preventing or detecting unauthorized modifications | Verifying a file's cryptographic hash |
| Availability | Ensuring information and services remain accessible | Maintaining recoverable backups |

Cryptography directly supports confidentiality and integrity, and can support authentication and availability-related security mechanisms. However, cryptography alone does not guarantee all three properties.

## 3. Encryption vs Hashing vs Encoding

These three concepts are different and should not be confused.

| Property | Encryption | Hashing | Encoding |
|---|---|---|---|
| Primary purpose | Confidentiality | Integrity verification and fingerprinting | Data representation or compatibility |
| Secret key required | Yes | No, for ordinary cryptographic hashes | No |
| Reversible | Yes, with the correct key and algorithm | Not designed to be reversible | Usually |
| Protects confidentiality | Yes, when correctly implemented | No | No |
| Example | AES | SHA-256 | Base64 |

### Encryption

Encryption transforms plaintext into ciphertext using an algorithm and a key.

```text
Plaintext + Key → Encryption → Ciphertext
Ciphertext + Key → Decryption → Plaintext
```

Example: Encrypting a confidential document so unauthorized users cannot read its contents.

### Hashing

Hashing transforms input data into a fixed-length digest.

```text
Input Data → Hash Function → Hash Digest
```

Example:

```text
Input:  hello
SHA-256:
2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
```

Even a small change to the input normally produces a different digest.

### Encoding

Encoding changes how data is represented so it can be stored or transmitted in a particular format.

Example:

```text
Text: Hello
Base64: SGVsbG8=
```

Base64 is not encryption. Anyone can decode it without a secret key.

**Security takeaway:** Encoding does not provide confidentiality, and hashing is not a substitute for encryption.

## 4. Symmetric Encryption

Symmetric encryption uses the same secret key for encryption and decryption.

```text
Plaintext
    |
    v
Encryption + Secret Key
    |
    v
Ciphertext
    |
    v
Decryption + Same Secret Key
    |
    v
Plaintext
```

### AES — Advanced Encryption Standard

AES is a widely used symmetric block cipher standardized by NIST.

AES supports three key sizes:

| Variant | Key Size |
|---|---:|
| AES-128 | 128 bits |
| AES-192 | 192 bits |
| AES-256 | 256 bits |

AES uses a 128-bit block size.

Common applications include:
- Full-disk encryption.
- File and database encryption.
- Secure communication protocols.
- Protecting stored sensitive information.

AES is a cryptographic algorithm, not an entire encryption system. Secure implementation also depends on the operating mode, key management, nonce or initialization-vector requirements, and authentication.

### Other Symmetric Algorithms

- **ChaCha20:** A stream cipher commonly used with Poly1305 for authenticated encryption.
- **3DES:** An older block cipher that is no longer recommended for new applications.
- **DES:** An obsolete cipher with an inadequate key size for modern security.

For new systems, use established, modern authenticated-encryption constructions rather than designing your own cryptographic scheme.

## 5. Asymmetric Cryptography

Asymmetric cryptography uses a mathematically related public key and private key.

- **Public key:** Can generally be shared with others.
- **Private key:** Must be protected by its owner.

Different asymmetric algorithms support different operations, including encryption, digital signatures, and key establishment.

### Basic Concept

```text
Public Key  → Shared openly
Private Key → Kept secret
```

For an encryption scheme that supports public-key encryption:

```text
Sender encrypts using recipient's public key
                 |
                 v
             Ciphertext
                 |
                 v
Recipient decrypts using recipient's private key
```

Only the corresponding private key should be able to decrypt the ciphertext under the scheme's security assumptions.

### Common Asymmetric Algorithms

| Algorithm | Main Uses |
|---|---|
| RSA | Digital signatures and, with suitable schemes, public-key encryption |
| ECC | Public-key cryptography using elliptic curves |
| ECDSA | Digital signatures |
| ECDH | Key agreement |
| Ed25519 | Digital signatures |
| X25519 | Key agreement |

**Important:** RSA encryption and RSA digital signatures are different operations. Likewise, ECDH and X25519 are used for key agreement, not for directly encrypting arbitrary files.

### Symmetric vs Asymmetric Cryptography

| Feature | Symmetric | Asymmetric |
|---|---|---|
| Keys | Shared secret key | Public/private key pair |
| Typical performance | Fast for bulk data | Generally more computationally expensive |
| Key distribution | Secret must be shared securely | Public key can be distributed openly, but its authenticity must be established |
| Common uses | File and disk encryption | Key establishment and digital signatures |

Modern secure communication often combines both approaches: asymmetric cryptography helps establish or authenticate keys, and symmetric cryptography protects the actual data.

## 6. Cryptographic Hash Functions

A cryptographic hash function generates a fixed-length digest from input data.

### Properties of a Secure Hash Function

1. **Deterministic:** The same input produces the same digest.
2. **Preimage resistance:** Given a digest, it should be computationally infeasible to find an input producing it.
3. **Second-preimage resistance:** Given an input, it should be infeasible to find a different input with the same digest.
4. **Collision resistance:** It should be infeasible to find any two distinct inputs with the same digest.

### Common Hash Algorithms

| Algorithm | Digest Size | Status |
|---|---:|---|
| MD5 | 128 bits | Cryptographically broken for collision resistance |
| SHA-1 | 160 bits | Deprecated for security-sensitive collision-resistant applications |
| SHA-256 | 256 bits | Widely used |
| SHA-512 | 512 bits | Widely used |
| SHA-3-256 | 256 bits | Standardized alternative hash function |

MD5 and SHA-1 should not be used where collision resistance is required for security.

### Example: Verify a Downloaded File

On Linux:

```bash
sha256sum downloaded_file.zip
```

On Windows PowerShell:

```powershell
Get-FileHash .\downloaded_file.zip -Algorithm SHA256
```

Compare the calculated digest with a trusted reference digest obtained independently.

A matching digest provides evidence that the file matches the reference. It does not prove that the file is safe or trustworthy if the reference itself is malicious or compromised.

### Hashing in DFIR

Cryptographic hashes are important in digital forensics because they help investigators:

- Identify files.
- Compare evidence copies.
- Detect changes to collected files.
- Correlate files with known samples.
- Document evidence integrity.

Record the hash algorithm, digest, file identity, and time of collection when appropriate.

## 7. Password Hashing and Salting

Passwords should not normally be stored as plaintext or protected only with a fast general-purpose hash such as SHA-256.

Password-storage systems should use dedicated password-hashing algorithms that make guessing more expensive.

### Salt

A salt is a unique, non-secret value used when deriving a password hash.

Salts help prevent identical passwords from automatically producing identical stored password hashes and reduce the effectiveness of precomputed rainbow tables.

### Recommended Password-Hashing Algorithms

- **Argon2id:** A modern memory-hard password-hashing option.
- **scrypt:** A memory-hard password-based key derivation function.
- **bcrypt:** A widely used adaptive password-hashing algorithm.
- **PBKDF2:** A password-based key derivation function with configurable iterations.

Use a maintained library and current security recommendations to choose parameters.

### Example Concept

```text
Password + Unique Salt + Work Factor
                 |
                 v
       Password-Hashing Function
                 |
                 v
          Stored Verifier
```

When a user logs in, the system derives a verifier from the submitted password and stored parameters, then checks whether it matches.

**Important:** Password hashing is intentionally designed to make guessing expensive. Ordinary fast hashes are suitable for many file-integrity tasks but are not ideal for password storage.

## 8. Digital Signatures

A digital signature helps establish the authenticity and integrity of signed data.

The signer uses a private signing key to create the signature. A verifier uses the corresponding public key to check it.

```text
Data + Private Signing Key
            |
            v
     Digital Signature

Data + Signature + Public Key
            |
            v
       Verification
```

A valid signature supports the conclusion that the signed data has not changed since signing and that the signature was generated by someone possessing the corresponding private key, subject to the security of the algorithm and key.

Digital signatures do not inherently provide confidentiality.

### Common Applications

- Software and update verification.
- Signed documents.
- Certificate-based authentication.
- Secure code distribution.
- Evidence and log authenticity mechanisms.

## 9. Digital Certificates and PKI

A digital certificate binds an identity or set of identities to a public key, with that binding attested to by a certificate issuer.

### PKI — Public Key Infrastructure

PKI includes the policies, processes, keys, certificates, and systems used to manage public-key identities and trust.

### Certificate Authority (CA)

A CA issues and signs certificates according to its procedures and applicable policies.

### Certificate Chain

A typical certificate chain includes:

```text
Root CA
   |
   v
Intermediate CA
   |
   v
Server Certificate
```

A client validates the certificate chain against its trust configuration and checks relevant properties such as validity dates, hostname, key usage, and revocation status where applicable.

### Why Certificates Matter in Cybersecurity

- HTTPS server authentication.
- Enterprise authentication.
- Code signing.
- Secure email.
- Certificate-based device identity.

A certificate's presence does not automatically mean a website or file is harmless. Investigators must consider the certificate's issuer, identity, validity, usage, and context.

## 10. TLS and HTTPS

TLS stands for Transport Layer Security. It protects communication between endpoints by supporting confidentiality, integrity, and authentication, depending on the protocol configuration and validation.

HTTPS is HTTP carried over TLS.

### Simplified TLS Workflow

1. The client connects to the server.
2. The client and server negotiate protocol parameters and cryptographic algorithms.
3. The server presents its certificate when required by the selected handshake.
4. The client validates the server's identity and certificate.
5. The endpoints establish shared traffic keys.
6. Application data is exchanged using authenticated encryption.

Modern TLS versions use key-establishment mechanisms and symmetric traffic encryption to protect communication efficiently.

### TLS Security Notes

- TLS 1.2 and TLS 1.3 are the principal modern TLS versions.
- SSL and older TLS versions are obsolete or unsuitable for modern secure configurations.
- Certificate validation is essential to prevent many man-in-the-middle attacks.
- TLS protects traffic in transit but does not prevent all malicious activity at the endpoints.

## 11. Digital Forensics and Cryptography

Cryptographic concepts are frequently encountered during DFIR investigations.

### File Hashing

Calculate hashes before and after transferring evidence when appropriate to help verify that the evidence copy has not changed.

### Encrypted Files

Investigators may encounter encrypted archives, disks, backups, or communication records.

The presence of encrypted data does not itself indicate malicious activity. Encryption is common in legitimate business and personal use.

### Ransomware Investigations

Ransomware may use cryptographic algorithms to encrypt victim files and may employ public-key cryptography to protect the keys used for file encryption.

Investigators should:
- Preserve affected systems and relevant evidence.
- Identify the ransomware family when possible.
- Collect ransom notes and encrypted-file samples safely.
- Examine process execution, persistence, and network activity.
- Search for applicable trusted decryptors and recovery guidance.
- Avoid modifying original evidence.

Never assume that encrypted files can be recovered without the necessary keys, a valid decryptor, or another viable recovery mechanism.

### File Integrity Verification

Hashes can help determine whether collected files match earlier copies or known reference samples.

However, a hash alone does not reveal who created a file, when it was created, or whether it is malicious. Those questions require additional evidence.

## 12. Common Cryptographic Attacks

| Attack | Explanation |
|---|---|
| Brute-force attack | Tries possible keys or passwords until a match is found |
| Dictionary attack | Tests candidate passwords from a wordlist |
| Rainbow-table attack | Uses precomputed hash lookup data against susceptible password-storage schemes |
| Collision attack | Attempts to find two distinct inputs with the same hash |
| Man-in-the-middle (MITM) | Intercepts or manipulates communication between parties |
| Replay attack | Reuses previously captured messages or authentication data |
| Downgrade attack | Attempts to force weaker protocol or algorithm choices |
| Side-channel attack | Exploits information leaked through timing, power consumption, cache behavior, or other implementation effects |

### How to Reduce Risk

- Use modern, standardized algorithms.
- Protect secret and private keys.
- Use multi-factor authentication where appropriate.
- Store passwords with dedicated password-hashing algorithms.
- Validate certificates and server identities.
- Keep cryptographic libraries and systems updated.
- Disable obsolete protocols and weak cipher configurations.
- Use authenticated encryption rather than encryption without integrity protection.

## 13. Important Cryptography Terms

| Term | Definition |
|---|---|
| Plaintext | Original readable or unencrypted data |
| Ciphertext | Data produced by encryption |
| Key | Value used by a cryptographic algorithm |
| Keyspace | Set of possible keys |
| IV | Initialization vector used by certain cryptographic modes |
| Nonce | Value intended to be used according to a scheme's uniqueness requirements |
| Salt | Non-secret random or unique value used in password hashing or key derivation |
| Digest | Output of a hash function |
| Entropy | Measure of uncertainty in a random variable |
| Key exchange / agreement | Process by which parties establish shared secret material |
| Digital signature | Cryptographic mechanism for verifying signed data |
| Certificate | Structure binding identity information to a public key |
| PKI | Infrastructure for managing public-key identities and trust |
| KDF | Key derivation function |
| HMAC | Keyed-hash message authentication code |

## 14. Practical Exercises

Perform these exercises on your own system or in an authorized lab.

### Exercise 1: Calculate a File Hash

Linux:

```bash
sha256sum sample.txt
```

Windows PowerShell:

```powershell
Get-FileHash .\sample.txt -Algorithm SHA256
```

Change one character in a test file and calculate its hash again. Compare the two digests.

### Exercise 2: Encode and Decode Base64

Linux:

```bash
printf 'Hello' | base64
printf 'SGVsbG8=' | base64 -d
```

Observe that Base64 is reversible without a key.

### Exercise 3: Inspect a Website Certificate

Open a website using HTTPS in your browser and inspect its certificate details.

Record:
- Subject or domain names.
- Issuer.
- Validity period.
- Public-key information.
- Certificate chain.

### Exercise 4: Compare File Hashes

Calculate the SHA-256 hash of a file before and after copying it to another directory.

Check whether the hashes match. This illustrates how hashes can support integrity verification.

### Exercise 5: Study Password Storage

Research how Argon2id uses memory and computation to make password guessing more expensive than using a fast general-purpose hash.

Do not test password-cracking tools against accounts or password databases without explicit authorization.

## 15. Reliable References

1. **NIST Cryptographic Standards and Guidelines:**  
   https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines

2. **NIST FIPS 197 — Advanced Encryption Standard (AES):**  
   https://csrc.nist.gov/pubs/fips/197/final

3. **NIST FIPS 180-4 — Secure Hash Standard:**  
   https://csrc.nist.gov/pubs/fips/180-4/upd1/final

4. **NIST FIPS 186-5 — Digital Signature Standard:**  
   https://csrc.nist.gov/pubs/fips/186-5/final

5. **RFC 8446 — TLS 1.3:**  
   https://www.rfc-editor.org/rfc/rfc8446

6. **RFC 4648 — Base16, Base32, and Base64 Data Encodings:**  
   https://www.rfc-editor.org/rfc/rfc4648

7. **OWASP Password Storage Cheat Sheet:**  
   https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html

8. **OWASP Cryptographic Storage Cheat Sheet:**  
   https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html

9. **NIST Digital Identity Guidelines:**  
   https://pages.nist.gov/800-63-4/

---

*Purpose: Cybersecurity study notes covering cryptographic fundamentals, secure communications, password protection, and digital forensics and incident response (DFIR). Always consult current standards and trusted library documentation before implementing cryptographic systems.*

