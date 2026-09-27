# CRYPTOTRACE — Tech Stack & Reasons

| Layer                 | Technology                          | Why We Use It                                                                |
| --------------------- | ----------------------------------- | ---------------------------------------------------------------------------- |
| **Frontend**          | **React + TypeScript**              | Interactive, type-safe dashboard and secure document viewer                  |
| **UI**                | **Tailwind CSS**                    | Fast, consistent and responsive interface development                        |
| **PDF Rendering**     | **PDF.js**                          | Controlled browser-based PDF rendering                                       |
| **Backend**           | **Python + FastAPI**                | High-performance APIs with easy integration of AI, CV and cryptography       |
| **Database**          | **PostgreSQL**                      | Reliable storage for users, sessions, policies and metadata                  |
| **File Storage**      | **MinIO / Encrypted Storage**       | Secure storage of encrypted documents and forensic evidence                  |
| **Computer Vision**   | **OpenCV + NumPy + SciPy + Pillow** | Perspective correction, image preprocessing and watermark extraction         |
| **AI/ML**             | **PyTorch**                         | Neural watermarking and advanced forensic image processing when required     |
| **Watermarking**      | **DWT / DCT / SVD / QIM**           | Robust invisible watermarking; algorithms can be experimentally compared     |
| **Error Correction**  | **Reed-Solomon ECC**                | Recovers watermark data damaged by compression, printing, scanning or noise  |
| **Hashing**           | **SHA-256 / SHA-3**                 | Document and evidence integrity verification                                 |
| **Key Derivation**    | **HKDF**                            | Generates unique session-specific fingerprints                               |
| **PQC**               | **ML-DSA**                          | Post-quantum signing and verification of provenance events                   |
| **DLT**               | **Hyperledger Fabric**              | Permissioned, tamper-evident provenance suitable for controlled environments |
| **Chaincode**         | **Go**                              | Efficient implementation of Fabric smart contracts                           |
| **Security**          | **RBAC + Zero Trust**               | Controlled access based on user, device and policy                           |
| **Infrastructure**    | **Any OS + Podman/Docker**           | Reproducible and deployable offline/air-gapped environment                   |
| **Security Hardware** | **TPM / HSM**                       | Hardware-backed protection of sensitive keys in advanced deployments         |

## Why This Stack?

```text
React + TypeScript
        ↓
User Interface
        ↓
FastAPI + Python
        ↓
Security + AI + Computer Vision
        ↓
SHA-256 + HKDF + ML-DSA
        ↓
Cryptographic Fingerprint
        ↓
DWT/DCT/SVD + ECC
        ↓
Invisible Robust Watermark
        ↓
OpenCV + PyTorch
        ↓
Forensic Recovery
        ↓
Hyperledger Fabric
        ↓
Tamper-Evident Provenance
```

### The main reason for the stack

**Python is the core technology** because CRYPTOTRACE's hardest components—**cryptography, watermarking, computer vision, forensic recovery and ML**—have strong Python ecosystems.

**React/TypeScript** handles the user-facing system, while **PostgreSQL/MinIO** handle data and encrypted files, and **Hyperledger Fabric + ML-DSA** provide the cryptographically verifiable provenance layer.


# CRYPTOTRACE — Implementation & Methodology

### Technology Architecture

```text
┌─────────────────────────────────────────────┐
│              PRESENTATION LAYER             │
│       React + TypeScript + Tailwind         │
│       Dashboard │ Secure Viewer │ Console   │
└──────────────────────┬──────────────────────┘
                       ↓
┌─────────────────────────────────────────────┐
│              APPLICATION LAYER              │
│                Python + FastAPI             │
│       Auth │ RBAC │ API │ Session Mgmt      │
└───────────────┬──────────────┬──────────────┘
                ↓              ↓
       ┌────────────────┐ ┌──────────────────────┐
       │ DATA & STORAGE │ │ CRYPTOGRAPHIC LAYER  │
       │ PostgreSQL     │ │ SHA-256 │ HKDF       │
       │ MinIO          │ │ ML-DSA │ ECC         │
       └───────┬────────┘ └──────────┬───────────┘
               │                     ↓
               │          ┌──────────────────────┐
               │          │ WATERMARKING ENGINE  │
               │          │ DWT/DCT/SVD + OpenCV │
               │          │ NumPy + PyTorch      │
               │          └──────────┬───────────┘
               │                     ↓
               │          ┌──────────────────────┐
               └─────────→│  FORENSIC ENGINE     │
                          │ OpenCV + PyTorch      │
                          │ Detect → Extract → ECC│
                          └──────────┬───────────┘
                                     ↓
                          ┌──────────────────────┐
                          │ PROVENANCE LAYER     │
                          │ Hyperledger Fabric   │
                          │ + Go Chaincode       │
                          └──────────┬───────────┘
                                     ↓
                          ┌──────────────────────┐
                          │ VERIFICATION LAYER   │
                          │ Hash + ML-DSA + DLT  │
                          └──────────┬───────────┘
                                     ↓
                         VERIFIED / INCONCLUSIVE /
                              NOT VERIFIED
```

## Implementation Methodology

```text
1. Authenticate
      ↓
2. Authorize User + Device
      ↓
3. Retrieve Encrypted Document
      ↓
4. Generate Document Hash
      ↓
5. Generate Session Fingerprint using HKDF
      ↓
6. Encode Fingerprint using ECC
      ↓
7. Embed Invisible Watermark
      ↓
8. Render through Secure Viewer
      ↓
9. Digital / Print / Scan / Camera Distribution
      ↓
10. Capture Leaked Evidence
      ↓
11. OpenCV Forensic Preprocessing
      ↓
12. Extract + ECC Decode Watermark
      ↓
13. Recover Session Fingerprint
      ↓
14. Verify Document Hash
      ↓
15. Verify ML-DSA Signature
      ↓
16. Verify Hyperledger Fabric Record
      ↓
17. Generate Provenance Result
```

## Technology-wise Implementation

| Technology             | Implementation Method                                       |
| ---------------------- | ----------------------------------------------------------- |
| **React + TypeScript** | Build dashboard, secure viewer and forensic console         |
| **FastAPI**            | Connect all modules through secure APIs                     |
| **PostgreSQL**         | Store users, sessions, policies and metadata                |
| **MinIO**              | Store encrypted documents and evidence                      |
| **SHA-256**            | Generate document/evidence integrity hashes                 |
| **HKDF**               | Generate unique session fingerprints                        |
| **ECC**                | Add redundancy to fingerprint payload                       |
| **DWT/DCT/SVD**        | Embed invisible robust watermark                            |
| **OpenCV**             | Image correction, localization and watermark extraction     |
| **PyTorch**            | Advanced forensic/ML watermarking if experiments justify it |
| **ML-DSA**             | Sign and verify decryption provenance                       |
| **Hyperledger Fabric** | Store tamper-evident provenance records                     |
| **Go Chaincode**       | Define and validate provenance transactions                 |
| **TPM/HSM**            | Protect sensitive keys in advanced deployments              |

### Core Methodology

> **Authenticate → Authorize → Encrypt/Decrypt → Fingerprint → ECC → Watermark → Distribute → Recover → Verify → Record → Attribute**

This keeps the implementation focused on the project's central objective: **linking a recovered document artifact to a specific authorized decryption session through multiple independently verifiable evidence sources.**
