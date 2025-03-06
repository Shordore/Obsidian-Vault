
**1. Introduction to Hash Functions**

• **Definition:**

A hash function is a deterministic, one-way function that maps an arbitrary-length input (message) to a fixed-length output called a hash or digest.

• **Purpose:**

Hash functions provide data compression and act as a fingerprint for the input data, enabling integrity verification, message authentication, and various cryptographic protocols.

---

**2. Message Authentication Codes (MACs)**

• **Role of MACs:**

MACs are used to ensure message integrity and authenticity. They combine a cryptographic hash function with a secret key to produce a short authentication tag.

• **Operation:**

• A keyed hash function (often referred to as HMAC when following a standard construction) takes a message M and a secret key K to produce a MAC value, denoted as MACK(M).

• When a sender transmits a message, they append the MAC. The receiver, who knows the secret key, can recompute the MAC to verify that the message was not altered and indeed came from the authentic source.

• **Example:**

In a man-in-the-middle attack, without knowing the key K, an adversary cannot generate a valid MAC for a tampered message.

---

**3. Cryptographic Hash Functions: Core Properties**

  

Good cryptographic hash functions must satisfy several critical properties:

• **Preimage Resistance (One-Way Property):**

Given a hash output y, it is computationally infeasible to find any input x such that h(x) = y.

• **Second Preimage Resistance (Weak Collision Resistance):**

Given an input x, it is hard to find another input x’ (x ≠ x’) such that h(x) = h(x’).

• **Collision Resistance (Strong Collision Resistance):**

It is computationally infeasible to find any two distinct inputs i and j that produce the same hash value, i.e., h(i) = h(j).

• **Determinism:**

The same input always yields the same output.

• **Avalanche Effect:**

A small change in the input should produce a significantly different hash output, with no correlation to the original hash.

• **Efficiency:**

The hash function should be computationally efficient to compute, enabling fast processing even for large inputs.

---

**4. Hash Functions vs. MACs**

• **Hash Functions:**

• Take a message M and output a digest h(M) with the properties described above.

• Used for integrity checks, digital signatures, and as building blocks in various protocols.

• **MACs (Message Authentication Codes):**

• Incorporate a secret key into the hash computation to yield a keyed output MACK(M).

• Provide both integrity and authenticity because an adversary without the secret key cannot produce a valid MAC.

• Often implemented as HMAC, which stands for “Hash-based Message Authentication Code.”

---

**5. Hash Attacks and the Birthday Paradox**

  

**Preimage and Second Preimage Attacks**

• **Preimage Attack:**

An adversary tries to find an input that hashes to a specific digest. For an m-bit hash, this requires roughly 2^m attempts.

• **Second Preimage Attack:**

Given a specific input, the goal is to find a different input with the same hash. This also requires near 2^m operations, making it computationally infeasible for secure hash sizes.

  

**Collision Attacks and the Birthday Paradox**

• **Collision Attack:**

Finding any two distinct messages x and y such that h(x) = h(y). Due to the birthday paradox, the expected number of attempts to find a collision in an m-bit hash is approximately 2^(m/2), which is significantly lower than 2^m.

• **Birthday Attack:**

This attack exploits the birthday paradox; for example, with a 128-bit hash, a collision might be found in around 2^64 attempts.

• **Implications:**

This is why modern hash functions use larger digest sizes (e.g., SHA-256, SHA-512) to mitigate collision attacks.

---

**6. Practical Considerations and Examples**

• **Common Hash Functions:**

• **MD5 (128-bit digest):** Now considered insecure.

• **SHA-1 (160-bit digest):** Also deprecated due to vulnerabilities.

• **SHA-256 and SHA-512:** Part of the SHA-2 family and widely used for secure applications.

• **SHA-3:** The winner of the latest NIST competition (2015), offering an alternative design.

• **Practical Attacks:**

• **Birthday Attack Example:** Illustrates how finding collisions in a hash function is more feasible than brute-force preimage attacks, emphasizing the need for sufficient digest length.

• **Message Forgery:** Without the secret key, an adversary cannot produce a valid MAC, protecting against tampering in transmission.

• **Integration in Systems:**

Hash functions and MACs are essential in protocols for digital signatures, data integrity verification, and secure authentication. They form the backbone of many cryptographic systems and are used in combination with encryption to provide comprehensive security.

---

**Summary**

  

Lecture 9 provides a comprehensive exploration of cryptographic hash functions and their applications:

• **Hash Functions:**

Serve as one-way, deterministic functions that compress data to a fixed size, with strong properties such as preimage, second preimage, and collision resistance. They are fundamental for ensuring data integrity.

• **Message Authentication Codes (MACs):**

Extend the concept of hash functions by incorporating a secret key to provide data authenticity and integrity, thwarting forgery and tampering by adversaries.

• **Hash Attacks:**

The lecture explains both preimage and collision attacks, highlighting how the birthday paradox reduces the complexity of finding collisions and why secure hash functions must use sufficiently large output sizes.

  

This breakdown not only reinforces the theoretical properties required for secure hash functions but also illustrates their practical applications and the importance of using robust constructions (like HMAC) to secure data in real-world cryptographic systems.

---

_Reference:_