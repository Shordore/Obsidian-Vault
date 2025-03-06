
**1. Overview of Asymmetric Encryption and RSA**

• **Asymmetric Encryption Fundamentals:**

• Uses a pair of keys—a public key for encryption and a private key for decryption.

• Allows secure communication without prior key sharing.

• **RSA in Context:**

• RSA (Rivest, Shamir, Adelman) is the dominant public key algorithm.

• It is conceptually simple yet relies on deep number theory.

• The security of RSA is based on the difficulty of factoring large composite numbers (i.e., finding the prime factors of n).

• **Trapdoor Functions:**

• RSA employs a trapdoor function, which is easy to compute in one direction (modular exponentiation) but extremely hard to reverse (i.e., deducing the private key without factoring n).

---

**2. Basic Mathematical Concepts Underpinning RSA**

• **Modular Arithmetic:**

• Work is done within the set of integers modulo n (denoted as Zₙ).

• Examples:

• 5 mod 13 = 5

• 13 mod 5 = 3

• **Modular Inverses:**

• An integer y is the modular inverse of x modulo n if (x·y) mod n = 1.

• In a prime modulus system, every nonzero element has an inverse.

• **Coprimality:**

• Two integers are coprime if their greatest common divisor is 1.

• This property is essential for choosing the public exponent e.

• **Euler’s Totient Function (Φ):**

• For a prime p, Φ(p) = p − 1.

• For a composite number n = p·q (with p and q distinct primes), Φ(n) = (p − 1)(q − 1).

• Determines the number of integers less than n that are coprime with n.

• **Carmichael’s Totient Function (λ):**

• Provides a sometimes tighter bound than Euler’s function.

• Defined as the least common multiple (LCM) of (p − 1) and (q − 1) for n = p·q.

• Used in some variants of RSA for additional security considerations.

---

**3. RSA Key Generation Process**

1. **Select Primes:**

• Choose two distinct large prime numbers, p and q.

1. **Compute n:**

• Calculate n = p · q. This value is used as the modulus for both the public and private keys.

1. **Calculate Euler’s Totient:**

• Compute Φ(n) = (p − 1)(q − 1).

1. **Choose the Public Exponent (e):**

• Select an integer e such that 1 < e < Φ(n) and e is coprime with Φ(n).

• e becomes the public key exponent.

1. **Determine the Private Exponent (d):**

• Compute d as the modular inverse of e modulo Φ(n), meaning that (d · e) mod Φ(n) = 1.

• d is kept secret as the private key exponent.

  

• **Example:**

• Let p = 3 and q = 11, then n = 33 and Φ(n) = (3 − 1)(11 − 1) = 20.

• Choosing e = 7 (which is coprime with 20), we compute d such that 7·d mod 20 = 1; here, d = 3.

• Public key: (7, 33); Private key: (3, 33).

---

**4. RSA Encryption and Decryption**

• **Encryption:**

• To encrypt a plaintext message m, compute ciphertext c = mᵉ mod n using the public key.

• **Decryption:**

• To recover the plaintext, compute m = cᵈ mod n using the private key.

• **Illustrative Example:**

• With public key (7, 33) and private key (3, 33):

• Encrypt plaintext 4:

c = 4⁷ mod 33 → compute 4⁷ = 16384; 16384 mod 33 = 16.

• Decrypt ciphertext 16:

m = 16³ mod 33 → compute 16³ = 4096; 4096 mod 33 = 4.

---

**5. Security of RSA**

• **Fundamental Security Basis:**

• The difficulty of factoring n (the product of two large primes) underpins RSA’s security.

• Without knowing p and q, an attacker cannot compute Φ(n) and, in turn, cannot derive the private key d from the public key (e, n).

• **Key Size Considerations:**

• Larger key sizes (e.g., 2048 bits and above) are recommended to ensure security against advances in computational power and factorization techniques.

• **Potential Attacks:**

• **Brute-force Attacks:**

• Trying all possible private keys; impractical with sufficiently large key sizes.

• **Mathematical Attacks:**

• Direct factorization of n, or deriving d without computing Φ(n).

• **Probable-Message Attacks:**

• Enumerating possible plaintexts for small message spaces; mitigated by padding.

• **Timing and Side-Channel Attacks:**

• Exploiting variations in decryption time or physical characteristics (power consumption, EM emissions) to deduce key information.

• **Mitigation Strategies:**

• Use proper padding schemes (e.g., OAEP) to prevent certain chosen-plaintext attacks.

• Implement constant-time algorithms to resist timing attacks.

• Ensure that p and q are chosen such that they are not too close together, and that (p − 1) and (q − 1) contain large prime factors.

---

**Summary**

  

Lecture 7 provides a comprehensive exploration of RSA by:

• Explaining **asymmetric encryption fundamentals** and the role of RSA in secure communications.

• Covering the **mathematical foundations** essential for RSA, including modular arithmetic, coprimality, Euler’s Totient Function, and Carmichael’s function.

• Detailing the **RSA key generation process** and illustrating it with a concrete example.

• Describing the **encryption and decryption operations** of RSA and emphasizing the importance of trapdoor functions.

• Discussing the **security basis of RSA** and outlining potential attacks, along with strategies to mitigate them.

  

This deep dive into RSA not only clarifies how the algorithm works but also highlights why it has remained a cornerstone of public key cryptography.

---

_Reference:_