The **RSA algorithm** is the best known and most widely used asymmetric (public-key) cryptographic scheme, essential for secure key exchange and digital signatures. It relies fundamentally on modular exponentiation and the mathematical difficulty of factoring large prime numbers.

***

## I. Introduction to Public Key Cryptography

Public Key Cryptography was developed to address the limitations of symmetric schemes, particularly regarding key distribution and non-repudiation.

*   Public Key Cryptography, also known as *asymmetric cryptography* or *two-key cryptography*, utilizes a pair of keys.
*   One key, the ***Public Key*** ($\text{PU}$), is made known to anybody and is used to encrypt messages or verify signatures.
*   The second key, the ***Private Key*** ($\text{PR}$), is known only to the recipient (owner) and is used to decrypt messages or create signatures.
*   It must be *computationally infeasible* to determine the private key from the public key.
*   Public key systems were developed to address two key issues: secure *key distribution* and *digital signatures* (providing authentication).
*   The two keys are mathematically related, but it is impossible/impractical to deduce one from the other.
*   Public key schemes typically rely on a *Trap-door One-Way Function*.
*   A *One-Way Function* $y = f(x)$ is easy to compute but infeasible to invert ($x = f^{-1}(y)$).
*   A ***Trap-door One-Way Function*** $y = f_K(x)$ is easy to compute, and $x = f_K^{-1}(y)$ is easy if the private key $K$ is known, but *infeasible* if only $y$ is known.

## II. The RSA Algorithm: Definition and Foundation

The RSA algorithm is a block cipher scheme whose security relies on the difficulty of factoring large integers.

*   The RSA scheme is a *block cipher scheme* where plaintext ($M$) and ciphertext ($C$) are integers between 0 and $n-1$ for some modulus $n$.
*   RSA was developed by *Rivest, Shamir, and Adleman* of MIT in 1977.
*   It is the best known and most widely used public key scheme based on *exponentiation* in a finite field over integers modulo $n$.
*   The security of RSA is highly dependent on the computational *cost of factoring large prime numbers*.
*   RSA typically utilizes large integers for $n$, often exceeding 1024 bits.
*   The process involves modular exponentiation, which is *computationally easy* when the relevant key is known.
*   The security of public-key schemes, like RSA, relies on the difference in difficulty between the *easy* encryption/decryption operation and the *hard* cryptanalysis (factoring) problem.
*   The three primary approaches to attack RSA are *Brute force key search*, *Mathematical attacks* (factoring), and *Timing attacks*.

## III. Detailed RSA Key Setup Algorithm

Each user generates their own public and private key pair by performing six essential steps, primarily revolving around large prime selection and modular arithmetic based on Euler's function $\phi(n)$.

*   **Step 1: Select Two Large Primes $p$ and $q$**: Choose two distinct, very large *prime numbers* ($p$ and $q$) at random.
*   **Step 2: Calculate the System Modulus $n$**: Compute the system modulus $n$ as the product of the two primes: $n = p \cdot q$.
*   **Step 3: Calculate Euler's Totient $\phi(n)$**: Calculate the Euler's Totient function $\phi(n)$ for the modulus: $\phi(n) = (p-1)(q-1)$.
*   **Step 4: Select the Public Exponent $e$**: Select an encryption key $e$ (public exponent) such that $1 < e < \phi(n)$ and *e is relatively prime to $\phi(n)$* ($\text{gcd}(e, \phi(n)) = 1$).
*   **Step 5: Determine the Private Exponent $d$**: Determine the decryption key $d$ (private exponent) by solving the congruence equation: $e \cdot d \equiv 1 \pmod{\phi(n)}$.
    *   This step finds the *modular multiplicative inverse* of $e$ modulo $\phi(n)$, where $0 \leq d < n$.
*   **Step 6: Publish and Keep Secret**: Publish the *Public Key* $\text{PU} = \{e, n\}$ and keep the *Secret Private Key* $\text{PR} = \{d, n\}$ secure.
*   The message $M$ must be an integer such that $0 \leq M < n$.

## IV. Mathematical Justification using Euler's Theorem

The mathematical correctness of the RSA decryption process is derived from Euler's Theorem, which establishes the required relationship between the exponents.

*   **Euler's Theorem** states that for every integer $a$ and integer $n$ that are *relatively prime* ($\text{gcd}(a, n)=1$), the following holds: $a^{\phi(n)} \equiv 1 \pmod n$.
*   The decryption key $d$ and encryption key $e$ are related such that $e \cdot d \equiv 1 \pmod{\phi(n)}$.
*   This relationship implies that $e \cdot d$ can be written in the form $1 + k \cdot \phi(n)$ for some integer $k$.
*   When the ciphertext $C$ is raised to the power of $d$, we obtain $M^{e \cdot d} \pmod n$.
*   Substituting the derived relationship: $M^{e \cdot d} = M^{1 + k \cdot \phi(n)} = M^1 \cdot M^{k \cdot \phi(n)} = M \cdot (M^{\phi(n)})^k \pmod n$.
*   Applying Euler's Identity $M^{\phi(n)} \equiv 1 \pmod n$, we get $M \cdot (1)^k \equiv M \pmod n$.
*   Therefore, $C^d \equiv M \pmod n$, confirming that decryption successfully recovers the original message $M$.

## V. The RSA Encryption Process

Encryption involves transforming the plaintext message $M$ into ciphertext $C$ using the recipient's public key components ($e, n$).

*   To encrypt a message $M$, the sender must first obtain the *recipient's public key* $\text{PU} = \{e, n\}$.
*   The message $M$ must be numerically represented as an integer such that $0 \leq M < n$.
*   If the message $M$ is larger than $n$, it must be broken down into smaller blocks and encrypted individually.
*   The encryption process involves calculating the ciphertext $C$ using the formula:
    $$C = M^e \pmod n$$
*   This process involves *modular exponentiation*, typically executed using fast exponentiation algorithms, taking $O(\log n^3)$ operations.
*   The resulting ciphertext $C$ is then transmitted to the intended recipient.
*   The opponent intercepting $C$ must attempt to find $M$ knowing only $C$, $e$, and $n$, a task infeasible without knowing the factoring of $n$.

## VI. The RSA Decryption Process

Decryption involves recovering the original plaintext message $M$ from the ciphertext $C$ using the recipient's secret private key ($d, n$).

*   To decrypt the ciphertext $C$, the owner uses their *private key* $\text{PR} = \{d, n\}$.
*   The decryption process involves calculating the plaintext $M$ using the formula:
    $$M = C^d \pmod n$$
*   Similar to encryption, decryption also relies on efficient modular exponentiation.
*   The decryption exponent $d$ is typically a large secret number, making the calculation $C^d \pmod n$ computationally easy for the recipient but computationally infeasible for an opponent who only knows $e$ and $n$.
*   Only the recipient who knows the secret private key $d$ can perform the modular exponentiation that effectively reverses the encryption process.

## VII. Detailed Example: RSA Key Setup

Using established parameters from the resource notes, we demonstrate the key generation process.

*   **Given Primes (Example from notes):** $p=17$ and $q=11$.
*   **1. Calculate Modulus $n$:**
    $$n = p \cdot q = 17 \cdot 11 = 187$$
*   **2. Calculate $\phi(n)$:**
    $$\phi(n) = (p-1)(q-1) = (17-1)(11-1) = 16 \cdot 10 = 160$$
*   **3. Select Public Exponent $e$:**
    Choose $e=7$. We check $\text{gcd}(7, 160) = 1$ (since 7 is prime and 160 is not divisible by 7).
    $$\text{Public Key } \text{PU} = \{7, 187\}$$
*   **4. Determine Private Exponent $d$:** Solve $e \cdot d \equiv 1 \pmod{\phi(n)}$, or $7 \cdot d \equiv 1 \pmod{160}$.
    We need to find $d$ such that $7d = 1 + 160k$.
    By inspection or Extended Euclidean Algorithm, $d=23$ is the solution.
    Check: $7 \cdot 23 = 161$. Since $161 = 1 \cdot 160 + 1$, $161 \equiv 1 \pmod{160}$.
    $$\text{Private Key } \text{PR} = \{23, 187\}$$

## VIII. Detailed Example: Encryption and Decryption

Using the generated keys $\text{PU}=\{7, 187\}$ and $\text{PR}=\{23, 187\}$, we encrypt a sample message $M=88$.

*   **Given Message:** $M=88$. Note that $0 \leq 88 < 187$.
*   **1. Encryption (Sender computes $C$):**
    $$C = M^e \pmod n$$
    $$C = 88^7 \pmod{187}$$
    To avoid direct calculation of $88^7$, we use properties:
    $$88^2 = 7744$$
    $$7744 \pmod{187} = 7744 - (41 \cdot 187) = 7744 - 7667 = 77$$
    $$88^4 \equiv 77^2 \pmod{187} = 5929 \pmod{187}$$
    $$5929 = 31 \cdot 187 + 132 \implies 88^4 \equiv 132 \pmod{187}$$
    $$88^7 = 88^4 \cdot 88^2 \cdot 88^1 \equiv 132 \cdot 77 \cdot 88 \pmod{187}$$
    $$132 \cdot 77 = 10164$$
    $$10164 \pmod{187} = 10164 - (54 \cdot 187) = 10164 - 10098 = 66$$
    $$C \equiv 66 \cdot 88 \pmod{187} = 5808 \pmod{187}$$
    $$5808 = 31 \cdot 187 + 11 \implies C = 11$$
    $$\text{Ciphertext } C = 11$$ (Matching result in notes)

*   **2. Decryption (Recipient computes $M$):**
    $$M = C^d \pmod n$$
    $$M = 11^{23} \pmod{187}$$
    $$11^{23} = 11^{1} \cdot 11^2 \cdot 11^4 \cdot 11^{16}$$ (Using binary decomposition of 23: $1+2+4+16$)
    We know $11^1 \equiv 11 \pmod{187}$.
    $11^2 = 121 \pmod{187}$.
    $11^4 \equiv 121^2 = 14641 \pmod{187}$
    $14641 = 78 \cdot 187 + 55 \implies 11^4 \equiv 55 \pmod{187}$.
    $11^8 \equiv 55^2 = 3025 \pmod{187}$
    $3025 = 16 \cdot 187 + 23 \implies 11^8 \equiv 23 \pmod{187}$.
    $11^{16} \equiv 23^2 = 529 \pmod{187}$
    $529 = 2 \cdot 187 + 155 \implies 11^{16} \equiv 155 \pmod{187}$.
    $$M \equiv 11^1 \cdot 11^2 \cdot 11^4 \cdot 11^{16} \pmod{187}$$
    $$M \equiv 11 \cdot 121 \cdot 55 \cdot 155 \pmod{187}$$
    $11 \cdot 121 = 1331$. $1331 \pmod{187} = 1331 - (7 \cdot 187) = 1331 - 1309 = 22$.
    $M \equiv 22 \cdot 55 \cdot 155 \pmod{187}$
    $22 \cdot 55 = 1210$. $1210 \pmod{187} = 1210 - (6 \cdot 187) = 1210 - 1122 = 88$.
    $M \equiv 88 \cdot 155 \pmod{187}$
    $M \equiv 13640 \pmod{187}$
    $13640 = 72 \cdot 187 + 88 \implies M = 88$
    The original plaintext $M=88$ is recovered.

## IX. Security Vulnerabilities and Attacks on RSA

The security of RSA is primarily threatened by the advancement of mathematical attacks aimed at factoring the modulus $n$.

*   ***Brute Force Key Search***: Trying all possible private keys is *theoretically possible* but *infeasible* given the large key space (e.g., 1024 bits).
*   ***Mathematical Attacks***: Focus on approaches to *factor the product of the two large prime numbers* $n=p \cdot q$.
    *   Once $p$ and $q$ are known, $\phi(n)$ can be easily calculated, allowing the attacker to determine the private key $d$ from the public key $e$.
    *   The primary defense is the selection of increasingly large prime numbers.
*   ***Timing Attacks***: These attacks depend on the *running time of the decryption algorithm*.
    *   The attacker measures the time taken by the victim's device to perform decryption based on the received ciphertext.
    *   Defenses include using *constant exponentiation time* and adding *random delays*.
*   The effectiveness of RSA relies on the disparity between the time complexity of encryption/decryption (polynomial time) versus the time complexity of factoring $n$ (super-polynomial time).
*   RSA requires the use of *large integers* to ensure factoring remains a hard problem.

## X. Public Key Exchange and Security Model

RSA is often integrated into a wider key management system and visualizes the use of asymmetric keys for secure communication.

*   RSA is frequently used not for direct data encryption (as it is slow compared to symmetric schemes) but for *encrypting secret keys* (session keys) used for symmetric encryption.
*   The encryption model shows that the Plaintext $X$ is encrypted using the *recipient's public key* $\text{PU}_B$ to produce $Y = E(\text{PU}_B, X)$.
*   The recipient decrypts using their *private key* $\text{PR}_B$: $X = D(\text{PR}_B, Y)$.
*   The security comparison highlights that, unlike conventional encryption where the key must be secret, in public key encryption, *only one of the two keys* (the private key) must be kept secret.
*   RSA also supports *Digital Signatures* by using the private key for encryption and the public key for verification.

**ASCII Diagram: RSA Encryption with Public/Private Key Pairs**

```ascii
Sender A                        Insecure Channel                        Receiver B
(Encrypts)                                                          (Decrypts)
      Plaintext M
          |
          V
     +-----------+
     | E(PUB)    |  <----- Uses B's Public Key (e, n)
     +-----------+
          |
          V
      Ciphertext C ----------------------------------------------> Ciphertext C
          |                                                            |
          |                                                            V
          |                                                       +-----------+
          |                                                       | D(PRB)    |  <----- Uses B's Private Key (d, n)
          |                                                       +-----------+
          |                                                            |
          +--------------------------------------------------------> Plaintext M
```
