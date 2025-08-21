
Security Fundamentals: Canvas-Friendly Study Guide
 
1. Cryptography Basics
Why it matters: Ensures confidentiality, integrity, and authenticity of data.
    •    Secret‑Key vs. Public‑Key
    ◦    Secret (Symmetric): One shared key to encrypt & decrypt. Fast, but key distribution is hard.
    ◦    Public (Asymmetric): Pair of keys (public + private). Anyone can encrypt with your public key; only you decrypt with your private key.
    •    Symmetric Ciphers & Modes
    ◦    Block Ciphers (e.g. AES): Encrypt data in fixed-size chunks (blocks).
    •    How it works: Plaintext is split into blocks (e.g. 128 bits), each block encrypted separately using the same key.
    •    Benefits: Fast in hardware; secure against bit-flipping attacks when used with proper mode.
    •    Drawbacks: Patterns in data can repeat if used alone (ECB), so need secure modes.
    ◦    Stream Ciphers (e.g. RC4, ChaCha20): Encrypt data one bit or byte at a time by XORing with a keystream.
    •    How it works: A pseudorandom keystream generator produces a sequence of bits; plaintext bits are XORed with this stream to get ciphertext.
    •    Benefits: Very efficient for streaming data; minimal latency, works well for real-time.
    •    Drawbacks: Reusing the same keystream key/IV can catastrophically compromise security (two-time pad).
    ◦    Modes of Operation (ECB, CBC, GCM): Define how to apply block ciphers across multiple blocks.
    •    ECB (Electronic Codebook): Encrypt each block independently.
    ▪    Benefit: Simple, parallelizable.
    ▪    Drawback: Identical plaintext blocks → identical ciphertext → leaks patterns.
    •    CBC (Cipher Block Chaining): Each plaintext block is XORed with the previous ciphertext block before encryption.
    ▪    Benefit: Hides patterns; tampering with one block garbles only that block.
    ▪    Drawback: Encryption is sequential (not parallel); requires an IV.
    •    GCM (Galois/Counter Mode): Counter mode for encryption plus built-in authentication tag (MAC).
    ▪    Benefit: Provides both confidentiality and integrity; parallel encryption.
    ▪    Drawback: More complex; incorrect IV reuse breaks both confidentiality and integrity.
    •    Hashing, MAC & HMAC
    ◦    Hash: A one‑way function that converts any input into a fixed-length “digest.” You can’t reverse it. Example: SHA‑256("hello") → 2cf24...; used to verify data integrity or store password digests.
    ◦    MAC (Message Authentication Code): A short code generated from a message and a secret key, ensuring both integrity and authenticity. Example: API requests include a MAC so the server knows they haven’t been tampered with and came from someone holding the key.
    ◦    HMAC: A specific type of MAC that combines a cryptographic hash and a secret key in a standardized way for extra security. Example: HMAC-SHA256 secures JSON Web Tokens and AWS request signatures.
    •    Digital Signatures
    ◦    Use your private key to sign a hash of the message.
    ◦    Verifier uses your public key to confirm who signed and that data wasn’t altered.
    ◦    Example: Alice wants to send an important note: “Meet at noon.” She hashes it, encrypts that hash with her private key (creating the signature), and sends both. Bob uses Alice’s public key to decrypt the signature and compares to his own hash; a match means the note is truly from Alice and unaltered.
$1
    •    Hash Chains: A series where each new hash input is the result of the previous hash—like links in a chain.
    •    How it works: Start with a secret value S₀. Compute H₁ = hash(S₀), H₂ = hash(H₁), H₃ = hash(H₂), … and so on.
    •    Use case: One-time passwords (OTPs). The server stores the final hash Hₙ; the client presents Hₙ₋₁, the server hashes it once and verifies the match, then updates the stored value. Each password is used only once.
    •    Benefits: Simple integrity check; secure against reversing if the hash is strong.
    •    Drawbacks: Server must track and update state; chain length is fixed in advance.
    •    Key Exchange (Diffie‑Hellman)
    ◦    A method for two parties to create a shared secret over an open channel without exposing it.
    •    How it works:
    1    Agree on public values: a large prime p and base g.
    2    Alice picks private a, computes A = gᵃ mod p; Bob picks private b, computes B = gᵇ mod p.
    3    They exchange A and B openly.
    4    Alice computes S = Bᵃ mod p; Bob computes S = Aᵇ mod p. Both derive the same secret S.
    •    Use case: Establishing secure session keys in protocols like TLS.
    •    Benefits: An eavesdropper who sees A and B cannot compute S without solving the discrete-log problem, which is computationally infeasible.
    •    Drawbacks: Vulnerable to man-in-the-middle attacks if identities aren’t authenticated; requires large parameters for security.
 
2. Authentication Fundamentals
Goal: Verify “who you are.”
    •    PKI (Public Key Infrastructure)
    ◦    Certificate Authorities issue digital certificates linking identities → public keys.
    ◦    Why we need it: Ensures that a public key truly belongs to its claimed owner, establishing trust for secure websites (HTTPS), encrypted email, and software signing.
    •    Credentials & Types
    ◦    Something you know: Passwords, PINs.
    ◦    Something you have: Smartcards, OTP tokens.
    ◦    Something you are: Biometrics (fingerprints, face).
 
3. Authentication Protocols
Use cases: Proving identity over a network.
    •    Kerberos
    1    Client authenticates to Key Distribution Center (KDC).
    2    KDC issues a Ticket‑Granting Ticket.
    3    Client uses that ticket to get service tickets for applications.
    •    ISO/OSI Protocol Vulnerabilities
    ◦    Older layers (e.g. Telnet, FTP) lack encryption or strong authentication—easily spoofed or intercepted.
    •    Securing Legacy Protocols
    ◦    Wrap in TLS/SSH, add strong mutual authentication, disable weak ciphers.
 
4. Firewalls
Purpose: Control inbound/outbound traffic.
    •    Blacklisting vs. Whitelisting
    ◦    Blacklist: Block known bad IPs/ports; everything else allowed.
    ◦    Whitelist: Allow only known good IPs/ports; everything else blocked.
    •    Firewall Policy
    ◦    Default‑deny: Block all, then explicitly allow needed traffic.
    ◦    Default‑allow: Allow all, then explicitly block unwanted traffic.
 
5. Intrusion Detection Systems (IDS)
Goal: Spot unauthorized or malicious activity.
    •    Network vs. Host‑Based
    ◦    Network IDS: Monitors traffic on a network segment.
    ◦    Host IDS: Monitors a single machine’s logs, processes, file changes.
    •    Signature‑Based vs. Behavior‑Based
    ◦    Signature: Matches known attack patterns.
    ◦    Behavior/Anomaly: Learns normal behavior; flags deviations.
    •    Bayesian Rate Fallacy
    ◦    A rare event in a large dataset can create many false positives—even with a good detector.
 
6. Software Security
Aim: Prevent attacks that exploit program flaws.
    •    Buffer Overflows
    ◦    What it is: Occurs when data writes beyond buffer limits, overwriting adjacent memory (e.g., return addresses).
    ◦    How it’s done: Attacker crafts input containing shellcode and an overwritten return pointer to redirect execution to their code.
    ◦    Example: Injecting 300 characters into a 256‑byte buffer, with the last bytes pointing to the malicious payload.
    ◦    Defense: Bounds checking, stack canaries, Data Execution Prevention (DEP), and Address Space Layout Randomization (ASLR).
    •    Heap Attacks
    ◦    What it is: Exploits flaws in heap memory management to corrupt metadata or objects.
    ◦    How it’s done: Attacker overflows or frees objects out‑of‑order to tamper with allocator metadata (e.g., freelist pointers), causing subsequent allocations to return pointers to attacker-controlled memory.
    ◦    Example: Fastbin dup attack in glibc where freed chunk pointers are manipulated to overwrite critical data.
    ◦    Defense: Hardened allocators (pointer encryption, integrity checks), safe memory allocators, and heap cookies.
    •    Return-Oriented Programming (ROP)
    ◦    What it is: Executes code by chaining small instruction sequences (“gadgets”) ending with ret, bypassing non-executable memory protections.
    ◦    How it’s done: Attacker identifies gadgets in existing binaries, then overflows a buffer to overwrite return addresses with a sequence of gadget addresses to perform desired actions.
    ◦    Example: Using gadgets like pop rdi; ret followed by a system call to spawn a shell.
    ◦    Defense: Control-Flow Integrity (CFI), shadow stacks, and more randomized ASLR.
    •    Memory & Code Safety
    ◦    What it is: Techniques to prevent unsafe memory operations and unauthorized code execution.
    ◦    How it’s done:
    •    Bounds Checking: Runtime/compile-time checks on buffer and array accesses.
    •    Safe Languages: Rust’s ownership and borrowing rules enforce safety at compile time, preventing use-after-free and buffer overflows.
    •    W^X (Write XOR Execute): Memory pages are flagged either writable or executable, never both, preventing injected code from executing.
    ◦    Example: Rust programs fail to compile if potential memory-safety violations are detected.
    ◦    Defense Benefits: Eliminates broad classes of vulnerabilities before code runs, reducing runtime exploitation risks.
    •    Access Control Models
    ◦    DAC: Owner decides access.
    ◦    MAC: System enforces based on labels.
    ◦    RBAC: Access rights tied to roles.