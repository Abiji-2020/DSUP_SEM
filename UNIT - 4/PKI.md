This detailed analysis addresses the structure, function, and application of Public Key Infrastructure (PKI), specifically detailing X.509 Certificates and the Secure Electronic Transaction (SET) protocol, providing comprehensive information suitable for a 14-mark response.

---

## Public Key Infrastructure (PKI) and Applications: Detail X.509 Certificates and Secure Electronic Transaction (SET)

### I. Public Key Infrastructure (PKI) Definition and Core Elements

**Public Key Infrastructure (PKI)** is the comprehensive set of hardware, software, people, policies, and procedures required to create, manage, store, distribute, and revoke **digital certificates** based on **asymmetric cryptography**.

#### A. Principal Role
*   The primary role of PKI is to enable the **secure, convenient, and efficient acquisition of public keys**.
*   It provides the framework necessary for applications such as S/MIME, SSL/TLS, IP Security, and SET.

#### B. Key PKI Elements (PKIX Model)
1.  **Certification Authority (CA):** The trusted entity responsible for **issuing certificates** and Certificate Revocation Lists (CRLs).
2.  **Registration Authority (RA):** An optional component that assists the CA, often handling **mutual authentication** during the initial user registration process.
3.  **End Entity:** A generic term denoting end users, devices, or servers that are identified in the subject field of a public key certificate.
4.  **Repository:** Any method used for **storing certificates and CRLs** so that end entities can retrieve them.

#### C. Example: Public Key Distribution via Certificates
Public Key Certificates allow key exchange without the need for **real-time access** to a Public Key Authority. A certificate binds the user's identity to their public key, and the entire content is **signed by a trusted CA**.

### II. PKI Management and Lifecycle Functions

PKIX (Public Key Infrastructure X.509) defines the core management functions necessary to maintain trust and operational security throughout the life of a certificate.

#### A. Core Management Functions
1.  **Registration:** The process where a user first **makes itself known to a CA** prior to certificate issuance, usually involving an offline or online procedure for **mutual authentication**.
2.  **Certification:** The formal step where the CA issues a certificate for a user's public key and may post it to a repository.
3.  **Key Pair Update:** Key pairs need to be **periodically updated** and new certificates issued to maintain cryptographic strength.
4.  **Revocation Request:** Advised when a private key is assumed to be **compromised**, or if the user is **no longer certified by the CA** (e.g., due to name change or affiliation change).
5.  **Initialization:** Installing key materials that maintain the appropriate relationship with keys stored elsewhere in the infrastructure.

### III. X.509 Public-Key Certificates: Structure and Signing

The **X.509 standard** defines the framework for authentication services and specifies the standard **format for public-key certificates**.

#### A. Certificate Purpose
*   The certificate binds the identity of an entity (Subject) to its public key.
*   The format is widely used in various applications, including SSL/TLS and SET.

#### B. X.509 Certificate Structure
The certificate contains essential identity and validation fields, all protected by the CA's digital signature:

1.  **Version:** Specifies the version of the X.509 standard used.
2.  **Certificate Serial Number:** A unique identifier assigned by the CA.
3.  **Signature Algorithm Identifier:** Identifies the algorithm used by the CA to sign the certificate.
4.  **Issuer Name:** The distinguished name of the **Certificate Authority** that issued the certificate.
5.  **Period of Validity:** Defines the lifespan using **Not Before** and **Not After** dates.
6.  **Subject Name:** The identity of the end entity whose public key is certified.
7.  **Subject Public Key Information:** Contains the **public key** itself and parameters for its corresponding algorithm.
8.  **Signature:** The digital signature of the entire certificate content, generated using the CA’s private key.

#### C. Example: Certificate Signing Process
The CA ensures the integrity of the certificate by signing the content before issuance.

1.  The unsigned certificate content is input to a hash function $H$.
2.  The resulting **Hashcode (Message Digest)** is generated.
3.  The CA **encrypts the Hashcode with the CA’s private key ($\text{PR}_{CA}$)** to form the **Signature**.

***Example ASCII Diagram: X.509 Certificate Signing***
```ascii
       Unsigned Certificate Content
                 |
                 V
             [Hash Function H]
                 |
                 V
          Message Digest
                 |
                 V
     [Encryption with CA's Private Key PR_CA]
                 |
                 V
          Digital Signature (S)
                 |
                 V
     Signed Certificate (Content + S)
```

### IV. X.509 Authentication Procedures (One-Way)

The X.509 standard defines procedures for key exchange and authentication, ensuring **confidentiality** and **timeliness**.

#### A. One-Way Authentication Flow
This procedure allows sender $A$ to securely send data and a session key ($K_{ab}$) to recipient $B$ while authenticating $A$'s origin:

$$A \to B: A \{T\_A, \text{ID}_B, \text{Sgn Data}, E(PU\_B, K_{ab})\}_{E(PR\_A)}$$

*   **Signature:** The entire message is encrypted using A's private key ($\text{PR}_A$), providing **authentication** and **non-repudiation**.
*   **Timeliness:** The inclusion of a **timestamp ($T_A$)** is essential to prevent **replay attacks**.
*   **Confidentiality:** The temporary session key ($K_{ab}$) is encrypted using B's public key ($\text{PU}_B$).

#### B. Verification Steps
1.  B uses $A$'s public key ($PU_A$) to decrypt the outer signature, verifying the source and data integrity.
2.  B uses its own private key ($\text{PR}_B$) to decrypt $E(PU_B, K_{ab})$, recovering the shared session key $K_{ab}$.

### V. Secure Electronic Transaction (SET) Protocol

**Secure Electronic Transaction (SET)** is an **open encryption and security specification** designed to specifically protect **credit card transactions** conducted over the Internet.

#### A. Key Features of SET
1.  **Confidentiality of Information:** Protecting sensitive payment details.
2.  **Integrity of Data:** Ensuring that order and payment information are not altered.
3.  **Cardholder Account Authentication:** Verifying the customer's identity.
4.  **Merchant Authentication:** Verifying the merchant's legitimacy.
5.  **PKI Reliance:** SET relies on digital certificates based on **public key cryptography** for both the customer and the merchant.

#### B. Transaction Flow Example
The SET transaction involves multiple participants, including the Issuer and Certification Authority. Key steps include:

1.  The customer opens an account and receives a digital certificate.
2.  The customer places an order, and the order and payment details are sent.
3.  The merchant requests **payment authorization** from the acquiring bank.
4.  The merchant confirms the order and, subsequently, requests payment.

### VI. SET Dual Signature Mechanism

The **dual signature** is a mechanism essential to SET, designed to link two messages intended for different recipients while preserving the confidentiality of each.

#### A. Purpose
*   The mechanism links the **Order Information (OI)** (intended for the merchant) and the **Payment Information (PI)** (intended for the bank).
*   Its purpose is to **avoid misplacement of orders** by assuring that the payment instruction corresponds exactly to the order placed.

#### B. Generation Process
1.  The customer calculates the **Message Digest (MD)** of the OI and the PI **independently**.
2.  These two MDs are cryptographically combined (e.g., by hashing their concatenation).
3.  The customer signs the resulting combined message digest using their private key, creating the **dual signature**.

***Example ASCII Diagram: Dual Signature Linking OI and PI***
```ascii
[Order Info (OI)]      [Payment Info (PI)]
      |                       |
      V                       V
  [Hash H1]              [Hash H2]
      |                       |
  [MD_OI]  --- Concatenate ---> [MD_PI]
                                |
                                V
                       [Hash Function H_Combined]
                                |
                                V
                       [Final Combined MD]
                                |
                                V
            [Encryption w/ Customer's Private Key]
                                |
                                V
                         [Dual Signature]
```
