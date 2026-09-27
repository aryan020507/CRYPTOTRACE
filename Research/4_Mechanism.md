# CRYPTOTRACE —  Mechanism

The mechanism of CRYPTOTRACE is based on creating a **cryptographically linked identity for every authorized decryption session**, hiding that identity inside the document, and later recovering and verifying it from a leaked artifact.

                    CRYPTOTRACE MECHANISM

┌───────────────────────┐
│ 1. ENCRYPTED DOCUMENT │
└───────────┬───────────┘
            ↓
┌────────────────────────────┐
│ 2. USER + DEVICE           │
│    AUTHENTICATION          │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 3. AUTHORIZATION / POLICY  │
│    CHECK                   │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 4. CONTROLLED DECRYPTION   │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 5. SESSION FINGERPRINT     │
│                            │
│ Document Hash              │
│ + Recipient Pseudonym      │
│ + Session ID               │
│ + Nonce                    │
│ + Version / Policy         │
│          ↓                 │
│        HKDF                │
│          ↓                 │
│ Unique Fingerprint         │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 6. ECC + INTERLEAVING      │
│    Adds error resilience   │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 7. INVISIBLE WATERMARK     │
│    DWT/DCT/SVD + CV/ML     │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 8. SECURE DOCUMENT VIEWER  │
└───────────┬────────────────┘
            ↓
       DIGITAL / PHYSICAL
          DISTRIBUTION
            ↓
    ┌───────┴────────┐
    ↓                ↓
 Screenshot       Print
 Copy             ↓
 JPEG             Scan / Photo
    ↓                ↓
    └───────┬────────┘
            ↓
┌────────────────────────────┐
│ 9. LEAKED DIGITAL EVIDENCE │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 10. FORENSIC ENGINE        │
│                            │
│ Document Detection         │
│ Perspective Correction    │
│ Image Normalization       │
│ Watermark Localization    │
│ Watermark Extraction      │
└───────────┬────────────────┘
            ↓
┌────────────────────────────┐
│ 11. ECC DECODING           │
│     ↓                      │
│ Fingerprint Recovery       │
└───────────┬────────────────┘
            ↓
       ┌────┴─────┬──────────┐
       ↓          ↓          ↓
 Document Hash  ML-DSA    DLT Record
 Verification  Verify    Verification
       └──────────┬─────────┘
                  ↓
┌────────────────────────────┐
│ 12. MULTI-EVIDENCE         │
│     VERIFICATION            │
└───────────┬────────────────┘
            ↓
   ┌────────┼────────────┐
   ↓        ↓            ↓
VERIFIED  INCONCLUSIVE  NOT VERIFIED


## Mechanism in 5 Steps

### 1. Create

Every authorized decryption generates a **unique session fingerprint**.

### 2. Embed

The fingerprint is **ECC-protected and invisibly embedded** into the rendered document.

### 3. Survive

The watermark is designed and experimentally tested to survive transformations such as **screenshot, compression, printing, scanning and photography**.

### 4. Recover

If the document is leaked, the forensic engine **corrects the image, extracts the watermark and reconstructs the fingerprint**.

### 5. Verify

The recovered fingerprint is checked against:

**Document Hash + ML-DSA Signature + Permissioned DLT Record**

to produce:

> **VERIFIED / INCONCLUSIVE / NOT VERIFIED**

### Core mechanism

> **CRYPTOTRACE converts each authorized decryption session into a recoverable cryptographic fingerprint, embeds it invisibly into the document, and later uses forensic recovery plus independent cryptographic evidence to establish verifiable session provenance.**
