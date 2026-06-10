**Image Steganography System**

A desktop tool that conceals AES-encrypted messages inside PNG images using Least Significant Bit (LSB) substitution. The stego image appears visually identical to the original, while the payload remains cryptographically secure.

---

### Features

- **AES-256-CBC Encryption** — Military-grade symmetric encryption with PBKDF2-SHA256 key derivation (200,000 iterations) and random 16-byte salt/IV per message
- **LSB Substitution** — Embeds data into the least significant bits of RGB channels, minimizing visual distortion
- **Live Capacity Counter** — Real-time display of remaining image storage capacity during encoding
- **Password Strength Meter** — Instant visual feedback on password entropy
- **Histogram Analysis** — Compare image statistical distributions before and after embedding
- **Wrong Password Detection** — Clear error handling for invalid decryption attempts

---

### How It Works

1. **Encrypt** — User plaintext is encrypted with AES-256-CBC using a key derived from the password via PBKDF2-SHA256
2. **Embed** — Ciphertext is split into bits and distributed across the LSBs of the carrier image's RGB channels
3. **Extract** — LSBs are read back from the stego image and reassembled into the ciphertext
4. **Decrypt** — AES-256-CBC decrypts the ciphertext using the same password-derived key

---

### Supported Formats

| Format | Support |
|--------|---------|
| PNG    | ✅ Read & Write |
| BMP    | ✅ Read & Write |
| JPEG   | ❌ Not supported (lossy compression corrupts LSB data) |

---

### Limitations

- Payload capacity is strictly bounded by image dimensions (`width × height × 3` bits)
- Lossy formats (JPEG) are unsupported; conversion to PNG/BMP is required
- Advanced statistical steganalysis tools may detect LSB anomalies
- Audio/video carrier support is not implemented

---

### Future Improvements

- [ ] Steganalysis detection module
- [ ] Auto-conversion pipeline for JPEG → PNG
- [ ] Mobile application port
- [ ] Integration of post-quantum or hybrid encryption schemes

---

### Authors

- Mohamed Aziz Amri
- Mohamed Dhia Ben Kilani
- Elaa Chaaleb

*Information Assurance and Security — May 2026*
