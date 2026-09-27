# CRYPTOTRACE
It is a solution for the most common problem which is data leaking and no proper encryption for any data.

Cryptographic Attribution and Immutable Decryption Provenance for Multi-Recipient Encrypted Document Distribution

Decrypt. Trace. Recover. Verify.

CRYPTOTRACE is a security-focused research and prototype platform for
preserving verifiable provenance of sensitive documents after authorized
decryption, including digital and physical distribution channels.

1. Problem Statement

Traditional encryption protects a document before and during controlled
access, but after an authorized user decrypts, views, prints,
screenshots, photographs, or redistributes it, conventional encryption
and centralized audit logs may not provide sufficient forensic
provenance.

Key challenges: - Digital copying, screenshots and forwarding - Printing
and physical circulation - Photographing and scanning printed
documents - Static or visible watermarks - Centralized audit-log
tampering risk - Lack of session-specific forensic identity - Loss of
provenance across digital -> physical -> digital transformations -
Restricted or air-gapped environments - Need for post-quantum
cryptographic protection

2. Core Solution

CRYPTOTRACE combines:

Secure access + session-specific fingerprinting + robust invisible
watermarking + post-quantum signatures + permissioned provenance +
forensic recovery.

The core chain is:

Document
 -> Recipient
 -> Decryption Session
 -> Cryptographic Fingerprint
 -> Invisible Watermark
 -> Digital / Physical Distribution
 -> Forensic Recovery
 -> ML-DSA Verification
 -> Permissioned DLT
 -> Verifiable Provenance

3. What the System Proves

CRYPTOTRACE is designed to establish that a recovered artifact is
cryptographically associated with a particular authorized decryption
session.

It does not automatically prove who physically took a photograph or
performed a leak. Attribution refers to the authorized
decryption/session provenance represented by the recovered evidence.

4. High-Level Architecture

+--------------------------------------------------------------+
| PRESENTATION: React + TypeScript + Tailwind + PDF.js        |
| Dashboard | Secure Viewer | Forensic Console                |
+-------------------------------+------------------------------+
                                |
                                v
+--------------------------------------------------------------+
| APPLICATION: Python + FastAPI                                |
| Authentication | RBAC | Documents | Sessions | APIs        |
+----------------------+-------------------+-------------------+
                       |                   |
                       v                   v
              +----------------+   +---------------------------+
              | DATA & STORAGE |   | CRYPTOGRAPHIC LAYER       |
              | PostgreSQL     |   | SHA-256 / SHA-3           |
              | MinIO          |   | HKDF / ML-DSA / ECC       |
              +-------+--------+   +------------+--------------+
                      |                         |
                      |                         v
                      |              +-------------------------+
                      |              | WATERMARKING ENGINE      |
                      |              | OpenCV / NumPy / PyTorch |
                      |              | DWT / DCT / SVD / QIM    |
                      |              +------------+-------------+
                      |                           |
                      |                           v
                      |              +-------------------------+
                      |              | FORENSIC ENGINE          |
                      |              | OpenCV / PyTorch         |
                      |              | Detection / Correction   |
                      |              | Extraction / ECC         |
                      |              +------------+-------------+
                      |                           |
                      +---------------------------+
                                  |
                                  v
                    +-----------------------------+
                    | PROVENANCE: Hyperledger     |
                    | Fabric + Go Chaincode       |
                    | Permissioned / Offline DLT  |
                    +-------------+---------------+
                                  |
                                  v
                    +-----------------------------+
                    | VERIFICATION                 |
                    | Watermark + Hash + ML-DSA   |
                    | + Ledger Consistency        |
                    +-------------+---------------+
                                  |
                                  v
                    VERIFIED / INCONCLUSIVE /
                         NOT VERIFIED

5. End-to-End Workflow

Encrypted Document
 -> Authentication
 -> Device Verification
 -> Authorization / Policy Check
 -> Controlled Decryption
 -> Session Fingerprint
 -> ECC + Interleaving
 -> Invisible Watermark
 -> Secure Rendering
 -> Digital / Physical Distribution
 -> Evidence Collection
 -> Forensic Recovery
 -> Watermark Extraction
 -> ECC Decode
 -> Fingerprint Recovery
 -> Document Hash + ML-DSA + DLT Verification
 -> Multi-Evidence Decision
 -> VERIFIED / INCONCLUSIVE / NOT VERIFIED

6. Technology Stack

Programming Languages

Python

TypeScript

Go

SQL

Bash

Frontend

React

TypeScript

Tailwind CSS

PDF.js

Axios

Lucide React

Backend

Python

FastAPI

Pydantic

SQLAlchemy

Computer Vision

OpenCV

NumPy

SciPy

Pillow

AI / ML

PyTorch

Cryptography

SHA-256 / SHA-3

HKDF

ML-DSA

Cryptographically secure random generation

Reed-Solomon ECC

Interleaving

Watermarking Candidates

DCT

DWT

SVD

QIM

Spread Spectrum

Hybrid DWT-DCT/SVD

Deep-learning watermarking

Database / Storage

PostgreSQL

MinIO / encrypted local storage

DLT

Hyperledger Fabric

Fabric CA

Go Chaincode

Private Data Collections

Infrastructure

Linux / Fedora

Podman or Docker

Git / GitHub

Offline / air-gapped LAN

7. Hardware

Prototype

Development workstation

16 GB+ RAM recommended

Modern multi-core CPU

NVIDIA GPU recommended for ML experiments

Printer

Flatbed scanner

Smartphone camera

Advanced / Production

TPM 2.0

HSM

Smart card / secure token

8. Cryptographic Fingerprint

A session-specific fingerprint is derived from cryptographic context:

F = HKDF(
    Document Hash
    + Recipient Pseudonym
    + Session ID
    + Nonce
    + Document Version
    + Policy Version
)

Example:

Document A + User A + Session 001 -> F1
Document A + User A + Session 002 -> F2

The fingerprint is encoded with ECC and transformed into a watermark
payload.

9. Watermarking Methodology

The final algorithm is selected experimentally rather than assumed in
advance.

DCT / DWT / SVD / QIM / Hybrid / Neural
                    |
                    v
              Attack Dataset
                    |
                    v
              Extraction
                    |
                    v
        BER / PSNR / SSIM / Recovery
                    |
                    v
          Select / Improve Algorithm

Digital attacks

JPEG, resize, crop, screenshot, blur, noise, brightness and contrast
changes.

Physical attacks

Print, scan, photocopy, print -> photograph, print -> scan.

Camera attacks

Perspective, rotation, lighting, shadow, blur, lens distortion, moiré
and compression.

10. Forensic Recovery

Leaked Evidence
 -> Evidence Hash
 -> Document Detection
 -> Corner / Perspective Detection
 -> Homography Correction
 -> Deskew / Normalization
 -> Noise / Lighting Processing
 -> Watermark Localization
 -> Extraction
 -> Deinterleaving
 -> ECC Decoding
 -> Fingerprint Recovery

11. ML-DSA Provenance

A decryption event is canonicalized and signed:

Decryption Event
 -> Canonicalization
 -> Hash
 -> ML-DSA Signature
 -> Provenance Record

ML-DSA is standardized by NIST in FIPS 204.

12. Permissioned DLT

Hyperledger Fabric is used for cryptographic provenance rather than
storing the full document.

Ledger data

Event ID

Document hash

Document version

Session ID

Recipient pseudonym

Watermark commitment

Policy version

Timestamp

ML-DSA signature

Previous event hash

Not stored directly on-chain

Full PDF

Plaintext sensitive document

Passwords

Private keys

Unnecessary personal information

13. Zero-Trust Security

User
 -> Authentication
 -> Device Verification
 -> Authorization
 -> Policy Evaluation
 -> Controlled Document Access

Controls can include RBAC, device identity, short-lived sessions, policy
authorization, audit logging and hardware-backed keys.

14. Multi-Evidence Verification

Recovered Watermark
       +
Document Hash
       +
ML-DSA Signature
       +
Ledger Consistency
       |
       v
Multi-Evidence Verification

VERIFIED

Fingerprint, ECC, document hash, signature and ledger evidence agree.

INCONCLUSIVE

Evidence is incomplete or too degraded for a reliable decision.

NOT VERIFIED

No valid matching provenance is established.

15. Research Methodology

Threat Model
 -> Watermark Baseline
 -> Attack Dataset
 -> Algorithm Benchmark
 -> Physical Validation
 -> Final Watermark Selection
 -> Cryptographic Provenance
 -> Forensic Engine
 -> DLT Integration
 -> End-to-End Validation

16. Dataset

The dataset should include: - Reports - Official letters - Forms -
Tables - Charts - Mixed text/image documents

Tracked metadata:

document_id
document_version
recipient_pseudonym
session_id
watermark_id
attack_type
attack_strength
original_image
watermarked_image
attacked_image
recovered_watermark
BER
PSNR
SSIM
detection_status
confidence

Dataset size should be determined by available prototype resources and
the experimental design.

17. Evaluation Metrics

Watermark

PSNR

SSIM

BER

Recovery rate

Detection rate

Forensics

False Attribution Rate (FAR)

False Rejection Rate (FRR)

Inconclusive Rate

Confidence

Cryptographic

ML-DSA verification success

Document hash match

Ledger consistency

Performance

Embedding time

Extraction time

Forensic inference time

Ledger transaction time

CPU/RAM usage

No final performance percentages should be claimed until they are
measured on the CRYPTOTRACE prototype.

18. Implementation Roadmap

Phase 0  -> Threat Model + Architecture
Phase 1  -> Authentication + RBAC + Document Management
Phase 2  -> Encryption + Secure Storage
Phase 3  -> Session Fingerprint + ECC
Phase 4  -> Watermark Baselines
Phase 5  -> Attack Simulator + Dataset
Phase 6  -> Print/Scan/Camera Experiments
Phase 7  -> Forensic Recovery Engine
Phase 8  -> ML-DSA Provenance
Phase 9  -> Hyperledger Fabric
Phase 10 -> Secure Viewer + Integration
Phase 11 -> Security + Performance Validation
Phase 12 -> SIH Demonstration

19. SIH MVP

The first demonstrable version should focus on:

Authentication
      +
Encrypted Document
      +
Session Fingerprint
      +
ECC
      +
Invisible Watermark
      +
Print / Photo Recovery
      +
ML-DSA Verification

Advanced extensions: - Hyperledger Fabric hardening - Neural
watermarking - TPM/HSM integration - Advanced policy engine -
Large-scale deployment

20. Feasibility

Infrastructure Reusability          Uses existing servers, secure
networks, printers, scanners and
IAM/PKI infrastructure

Scalable Deployment                 Modular architecture can scale from
department to multi-organization
deployment

Cost-Effectiveness                  Open-source components reduce
licensing requirements

Main technical risk: reliable fingerprint recovery after realistic
print -> scan/photo -> compression -> perspective -> lighting ->
crop transformations.

21. Viability

Proven Concept                      Built from established
cryptography, watermarking,
computer vision, Zero Trust and
permissioned-ledger technologies

Public Trust                        Provides verifiable provenance and
evidence integrity

Accountability                      Associates artifacts with
authorized decryption sessions

22. Business Model

CRYPTOTRACE follows a B2G + B2B cybersecurity model.

Government / Enterprises
          |
          v
   CRYPTOTRACE Platform
          |
    +-----+-----+---------+
    |           |         |
    v           v         v
 Licensing   Integration  Forensic
             Services     Services
    |           |         |
    +-----------+---------+
                |
                v
        Annual Maintenance
                |
                v
        Recurring Revenue

Potential revenue: - On-premise platform licensing -
Department/organization deployment - Annual maintenance and support -
IAM/PKI/HSM integration - Forensic investigation - Security and
watermarking upgrades

Potential cost savings: - Reduced manual investigation - Reduced audit
effort - Faster provenance analysis - Lower dependence on external/cloud
services in restricted environments

Actual savings and profitability should be established through pilot
deployments and cost studies.

23. Impact Sectors

Government & Public Sector

Confidential document provenance, traceability, auditability and secure
information exchange.

Defence & PSUs

Sensitive document distribution, strategic information protection and
air-gapped operation.

Banking & Finance

Financial document provenance, controlled sharing and regulatory
evidence.

Healthcare

Medical/research document traceability, patient-data protection and
compliance support.

Legal & Corporate

Evidence integrity and controlled document distribution.

Research & Academia

Research provenance, intellectual-property protection and controlled
collaboration.

24. Benefits

Enhanced document security

Session-level accountability

Automated forensic recovery

Digital + physical leak traceability

Tamper-evident provenance

Post-quantum signature support

Audit and compliance support

Offline/air-gapped operation

Reduced manual investigation effort

Integration with existing security infrastructure

25. Limitations

Watermark recovery is not guaranteed under every transformation.

Physical capture introduces uncontrolled variables.

AI watermarking requires representative training and validation
data.

DLT does not eliminate all operational security risks.

ML-DSA protects signatures, not the entire system.

A recovered fingerprint identifies an associated authorized session,
not necessarily the physical person who leaked the artifact.

Production deployment requires security testing, key-management
controls and appropriate certification.

External research results must not be presented as CRYPTOTRACE
performance.

26. Research Foundation

CRYPTOTRACE builds on established work in: - Post-quantum digital
signatures - Zero Trust architecture - Robust document watermarking -
Print-scan watermarking - Screen/camera-resilient watermarking -
Permissioned distributed ledgers - Computer vision - Error-correcting
codes

27. References

NIST FIPS 204 --- ML-DSA

https://csrc.nist.gov/pubs/fips/204/final

NIST SP 800-207 --- Zero Trust Architecture

https://csrc.nist.gov/pubs/sp/800/207/final

Hyperledger Fabric --- Private Data

https://hyperledger-fabric.readthedocs.io/en/latest/private-data-tutorial.html

Hyperledger Fabric --- Private Data Architecture

https://hyperledger-fabric.readthedocs.io/en/latest/private-data-arch.html

Robust PDF Watermarking against Print--Scan Attack

Li et al., Sensors, 2023. https://doi.org/10.3390/s23104698

Screen-Shooting Resilient Document Image Watermarking

Ge et al., 2022. https://arxiv.org/abs/2203.05198

28. Project Structure

CRYPTOTRACE/
├── frontend/
├── backend/
├── watermark-engine/
├── pqc/
├── forensic-engine/
├── ledger/
├── datasets/
├── experiments/
├── docs/
├── tests/
├── docker/
├── scripts/
├── .env.example
├── README.md
└── LICENSE

29. Development Principles

Security by design

Zero Trust

Privacy by design

Evidence before attribution

No fabricated performance claims

Experiment-driven watermark selection

Offline-first architecture

Modular services

Hardware-backed security for production

Fail-safe forensic decisions

30. Final Vision

Traditional document security:

Encrypt -> Authorize -> Decrypt -> END

CRYPTOTRACE:

Encrypt
  -> Authorize
  -> Session Fingerprint
  -> Invisible Watermark
  -> Digital / Physical Distribution
  -> Forensic Recovery
  -> Cryptographic Verification
  -> Verifiable Provenance

CRYPTOTRACE extends document security from access control to
cryptographically verifiable post-decryption provenance across digital
and physical distribution channels.