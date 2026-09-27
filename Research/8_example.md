Yes. A **recent Indian example can make the value of CRYPTOTRACE much clearer**. One particularly relevant case is the **2026 NEET-UG paper-leak investigation**, because it involved sensitive examination material being accessed by people involved in the examination process and then being disclosed before the exam.

## Real Indian Example: NEET-UG 2026 Paper Leak

In May 2026, the CBI registered a case concerning alleged unauthorized circulation of NEET-UG 2026 examination material. The official investigation said some people involved in the examination process had access to the questions and allegedly disclosed them during special coaching sessions before the exam. CBI subsequently identified and arrested people it described as sources of the Chemistry and Biology leaks. ([Press Information Bureau][1])

The important point for CRYPTOTRACE is this:

> **The problem was not simply unauthorized hacking. Sensitive information was allegedly exposed through people who had legitimate access to the examination material.**

That is exactly the type of **post-authorized-access provenance problem** CRYPTOTRACE is designed to address.

---

# How CRYPTOTRACE Could Have Helped

Imagine NTA uses CRYPTOTRACE to distribute the confidential examination material.

### Conventional approach

```text
              CONFIDENTIAL PAPER
                       ↓
                Encryption
                       ↓
              Authorized Person
                       ↓
                Decryption
                       ↓
              Question Paper
                       ↓
            ┌──────────┴──────────┐
            ↓                     ↓
        Legitimate             Leakage
        handling              / copying
```

Once the authorized person has decrypted the material, conventional encryption cannot by itself establish which particular decrypted session produced a leaked copy.

---

# With CRYPTOTRACE

The process would become:

```text
                  NEET QUESTION PAPER
                          ↓
                     SHA-256
                          ↓
                  Document Identity
                          ↓
              Authorization + Device Check
                          ↓
                     DECRYPTION
                          ↓
             ┌──────────────────────┐
             │ Session Fingerprint   │
             │                      │
             │ Document Hash        │
             │ Recipient ID         │
             │ Session ID           │
             │ Nonce                │
             │ Version              │
             │ Policy               │
             └──────────────────────┘
                          ↓
                    HKDF + ECC
                          ↓
              Invisible Watermark
                          ↓
                    Secure Viewer
                          ↓
               Authorized Handling
                          ↓
                  Potential Leakage
                          ↓
                Recovered Evidence
                          ↓
             Forensic Extraction
                          ↓
                Fingerprint Found
                          ↓
       ┌───────────────────────────────┐
       │ Document Hash Verification    │
       │ ECC Verification              │
       │ ML-DSA Signature Verification │
       │ Provenance/DLT Verification   │
       └───────────────────────────────┘
                          ↓
                  PROVENANCE RESULT
```

---

# Example With Multiple Authorized Officials

Suppose three authorized officials have access to the same examination document.

### Official A

```text
Question Paper
     +
Official A
     +
Session A-001
     ↓
Fingerprint F-A001
```

### Official B

```text
Question Paper
     +
Official B
     +
Session B-001
     ↓
Fingerprint F-B001
```

### Official C

```text
Question Paper
     +
Official C
     +
Session C-001
     ↓
Fingerprint F-C001
```

Although all three receive **the same question paper**, the decrypted/rendered copies carry different invisible forensic fingerprints.

---

# Suppose the Leak Happens

Imagine investigators later obtain a photograph, scan, screenshot, or digital copy of the leaked questions.

They submit it to CRYPTOTRACE:

```text
             LEAKED IMAGE
                  ↓
         Image Preprocessing
                  ↓
       Perspective Correction
                  ↓
        Watermark Localization
                  ↓
        Watermark Extraction
                  ↓
             ECC Decode
                  ↓
        Fingerprint = F-B001
                  ↓
          Provenance Lookup
                  ↓
          Session B-001
                  ↓
       Cryptographic Verification
                  ↓
             VERIFIED
```

The system could then report something like:

> **Recovered artifact corresponds to decryption session B-001 associated with authorized recipient B.**

It should **not** automatically state:

> "B leaked the paper."

That distinction is essential.

The recovered artifact may have been photographed, copied, or transferred by somebody else after the authorized session.

---

# Why This Is Different From Normal Audit Logs

Suppose normal logs say:

```text
10:02 AM — Official A opened document
10:07 AM — Official B opened document
10:13 AM — Official C opened document
```

After the leak, investigators still have to determine which access event corresponds to the leaked copy.

CRYPTOTRACE creates:

```text
Official A
    ↓
Session A001
    ↓
Fingerprint F-A001

Official B
    ↓
Session B001
    ↓
Fingerprint F-B001

Official C
    ↓
Session C001
    ↓
Fingerprint F-C001
```

The leaked artifact itself carries evidence that can be compared against those sessions.

---

# Another Very Relevant 2026 Indian Example: Kudankulam-Related Data Exposure

A second example is the **2026 reported cyber incident involving documents related to the Kudankulam Nuclear Power Project**.

Reports said a ransomware group published a large quantity of project-related files associated with a contractor. NPCIL subsequently stated that the leaked material did **not** involve nuclear safety/security systems and that the plant's critical systems were unaffected. ([@theweek][2])

This example is useful for explaining a different CRYPTOTRACE capability:

### Supply-chain document provenance

A large project can involve:

```text
NPCIL
   ↓
Contractors
   ↓
Subcontractors
   ↓
Engineers
   ↓
Project Teams
   ↓
Sensitive Documents
```

CRYPTOTRACE could provide provenance for sensitive documents shared with authorized parties:

```text
Central Organization
       ↓
Contractor A → Session A → Fingerprint A
       ↓
Contractor B → Session B → Fingerprint B
       ↓
Engineer C   → Session C → Fingerprint C
```

If a recovered document is found outside the authorized environment, investigators can attempt to recover the session fingerprint.

Again, CRYPTOTRACE **would not prevent the initial ransomware compromise by itself**. Its value would be in adding a provenance layer to documents that had previously been authorized for access/distribution.

---

# What CRYPTOTRACE Actually Prevents vs Helps Investigate

This is important for your SIH presentation.

| Threat                             | CRYPTOTRACE's role                                           |
| ---------------------------------- | ------------------------------------------------------------ |
| Unauthorized login                 | **Helps prevent** through authentication/authorization       |
| Unauthorized decryption            | **Helps prevent** through access policies                    |
| Unauthorized document export       | **Helps reduce** through controlled viewer/rendering         |
| Screenshot                         | **Makes recovered artifact potentially traceable**           |
| Photograph                         | **Attempts forensic recovery**                               |
| Printing                           | **Attempts print-resistant watermark recovery**              |
| Scanning                           | **Attempts watermark recovery**                              |
| Copying leaked file                | **Potentially preserves session fingerprint**                |
| Audit-log manipulation             | **Provides cryptographically verifiable provenance records** |
| Physical redistribution            | **Attempts to maintain provenance through watermarking**     |
| Ransomware                         | **Not a standalone ransomware-prevention system**            |
| Person physically leaking document | **Does not automatically prove physical identity**           |

So don't say:

> **"CRYPTOTRACE would have prevented the NEET paper leak."**

A technically defensible statement is:

> **"If CRYPTOTRACE had been deployed on the examination-document distribution workflow, each authorized decryption could have carried a unique cryptographic provenance fingerprint. If a recovered leaked copy retained sufficient watermark information, investigators could potentially associate it with the corresponding authorized decryption session."**

---

# The Powerful SIH Story

You can turn the example into a very strong presentation slide:

## **Real-World Problem → CRYPTOTRACE**

```text
        REAL-WORLD INCIDENT
                ↓
      Sensitive document accessed
                ↓
       Authorized person receives it
                ↓
          Information leaks
                ↓
       Investigation begins
                ↓
       "Who had access?"
                ↓
        Logs + interviews
                ↓
       Difficult attribution
```

### CRYPTOTRACE

```text
        Sensitive Document
                ↓
        Authorized Access
                ↓
       Unique Session ID
                ↓
     Cryptographic Fingerprint
                ↓
      Invisible Watermark
                ↓
        Digital / Physical
          Distribution
                ↓
          LEAKED ARTIFACT
                ↓
       Forensic Extraction
                ↓
       Fingerprint Recovery
                ↓
       ML-DSA Verification
                ↓
        DLT Verification
                ↓
       SESSION PROVENANCE
```

---

# The Key Innovation in One Sentence

> **CRYPTOTRACE shifts the investigation from "Who had access to the document?" to "Which authorized decryption session does the recovered artifact cryptographically correspond to?"**


