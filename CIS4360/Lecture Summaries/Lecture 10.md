
**1. Overview and Agenda**

• **Context:**

The lecture builds on earlier material by examining advanced uses of hash functions in authentication and digital signatures. It also highlights practical considerations such as hash attacks and key management.

• **Key Topics Covered:**

• Hash attacks (with a focus on message extension attacks)

• HMAC (Hash-based Message Authentication Code)

• Digital signatures and their properties

• An introduction to key agreement protocols

---

**2. Hash Attacks and the Need for Better MAC Constructions**

  

**Message Extension Attack**

• **Vulnerability in Direct Keyed Hashing:**

• Using a construction like MACₖ(M) = H(k || M) is vulnerable to extension attacks.

• **Attack Scenario:** An adversary who intercepts H(k || M) can append extra data M′ and, without knowing the secret key k, can compute H(k || M || M′) by leveraging the iterative (or Merkle–Damgård) structure of many hash functions.

• **Implication:**

• Because the hash function’s internal state can be continued, an attacker might extend the message and forge a valid MAC.

• **Solution Overview:**

• To counteract this, a mechanism is needed that prevents an attacker from extending the hash output without knowledge of the key.

---

**3. HMAC: A Robust MAC Construction**

  

**HMAC Definition and Structure**

• **Formula:**

HMAC(k, M) = H((k ⊕ opad) || H((k ⊕ ipad) || M))

Where:

• **k:** The secret key (padded to a fixed block size if necessary).

• **ipad:** The inner padding (a constant byte repeated to match the block size).

• **opad:** The outer padding (a different constant byte, similarly repeated).

• **H:** A cryptographic hash function (e.g., SHA-256).

• **Design Goals:**

• **Key Separation:** The inner and outer layers use the key in different masked forms (with ipad and opad), ensuring that even if the underlying hash function is vulnerable to extension attacks, the HMAC construction is not.

• **Security and Flexibility:**

• HMAC uses existing hash functions without modifying their core structure.

• It preserves performance and can be easily updated to use stronger hash functions if needed.

• **Advantages over Naïve Constructions:**

• Prevents message extension attacks because the key is mixed into both the inner and outer layers.

• Resistant against brute-force and birthday attacks to a degree consistent with the underlying hash function.

---

**4. Digital Signatures**

  

**Concept and Purpose**

• **Digital Signatures:**

• Are cryptographic schemes that enable a sender to sign a message with a private key, generating a signature that can be verified by anyone possessing the corresponding public key.

• They provide **authentication** (verifying the identity of the signer), **integrity** (ensuring the message has not been altered), and **non-repudiation** (preventing the signer from denying the signature).

  

**How Digital Signatures Work**

• **Signing Process:**

• Typically involves hashing the message and then encrypting the hash with the sender’s private key.

• The signature is attached to the message, and any recipient can verify it by decrypting the signature with the sender’s public key and comparing it to the hash computed over the received message.

• **Contrast with MACs:**

• **MACs** require a shared secret key between sender and receiver and only ensure message integrity and authenticity.

• **Digital Signatures,** however, use asymmetric cryptography so that the verification key (public key) is widely distributed, and the signer cannot later repudiate the signed message.

  

**Properties of Digital Signatures**

• **Authentication:**

Verifies that the message was indeed created by the holder of the private key.

• **Data Integrity:**

Confirms that the content has not been altered since signing.

• **Non-Repudiation:**

Provides evidence that the signer cannot deny having signed the message.

• **Implementation:**

Digital signatures are typically implemented using a combination of hash functions (to generate a digest) and asymmetric encryption (to sign the digest).

---

**5. Key Agreement (Brief Mention)**

• **Key Agreement Protocols:**

• While not the main focus of this lecture, key agreement mechanisms are mentioned as essential for securely establishing shared keys between parties.

• In practice, digital signatures and key agreement protocols often work together to secure communications.

---

**6. Other Uses of Hash Functions**

  

**Hash Authenticators and Hash Chains**

• **Hash Authenticators:**

• Using hash functions to generate authenticators (or tokens) for verifying messages.

• Example: A sender can precompute a hash value and later reveal a secret token that, when hashed, matches the precomputed value, ensuring message authenticity.

• **Hash Chains:**

• A sequence of hash computations where each output is the input for the next hash.

• **Applications:**

• Used in time-based authentication schemes, such as verifying sequential events (e.g., class cancellations).

• They offer a method for forward-secure authenticators where revealing an earlier value does not compromise future values.

  

**Pseudorandom Number Generators (PRNGs) Based on Hashes**

• **PRNGs:**

• Hash functions can also serve to build pseudorandom number generators by iteratively hashing a seed value.

• **Use Cases:**

• Generating random values for cryptographic purposes.

• Serving as a keystream in stream cipher applications.

---

**7. Summary**

  

Lecture 10 integrates several advanced topics related to the practical use of hash functions in ensuring data authenticity and integrity:

• **Hash Attacks and the Need for Secure MACs:**

• It discusses why naïve constructions (like HMACₖ(M) = H(k || M)) are vulnerable to message extension attacks.

• **HMAC as a Robust MAC Construction:**

• Details the HMAC construction, its formula, and how it mitigates extension attacks while preserving performance and allowing hash function flexibility.

• **Digital Signatures:**

• Explains the role of digital signatures in providing authentication, integrity, and non-repudiation, highlighting their reliance on cryptographic hash functions and asymmetric encryption.

• **Additional Applications of Hash Functions:**

• Briefly covers hash authenticators, hash chains, and PRNGs, showing the broader utility of hash functions in security protocols.

  

Together, these concepts demonstrate the critical role of hash functions not only as tools for data compression but also as essential components for secure authentication and digital communication in modern cryptographic systems.

---

_Reference:_