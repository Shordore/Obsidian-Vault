
**1. Attacks, Attack Vectors, and Attack Surfaces**

  

**Attack Definition and Types:**

• An **attack** is the deliberate execution of one or more steps aimed at exploiting a vulnerability to cause a security violation.

• **Types of attacks include:**

• **Passive attacks:** e.g., eavesdropping or sniffing network traffic.

• **Active attacks:** e.g., password guessing, tampering with packets.

• **Spoofing:** where an attacker impersonates another entity.

• **Denial of Service (DoS):** aimed at making services unavailable to legitimate users.

  

A **compromise** is said to occur when an attack succeeds, leading to unauthorized access or control over resources.

  

**Attack Vector vs. Attack Surface:**

• An **attack vector** is the method or pathway used by an adversary to breach a system (e.g., an unlocked door in a physical security analogy).

• The **attack surface** is the sum of all points where an attacker might attempt to enter or extract data (e.g., all the doors and windows of a house).

  

These distinctions help in understanding where vulnerabilities lie and how an attacker might exploit them. 

---

**2. Security Models and Threat Models**

  

**Security Models:**

• A **security model** combines trust and threat models to provide a set of security requirements for a system’s design.

• It ensures that a system has a coherent set of rules to enforce confidentiality, integrity, availability, authenticity, and other properties.

• A common pitfall is designing systems without an integrated security model, which can lead to vulnerabilities that are hard to retrofit later.

  

**Threat Models:**

• A **threat model** outlines the potential attackers (or adversaries) by defining their goals and capabilities.

• It helps system designers understand the various risks and design countermeasures that match the threat landscape.

• In our lecture, threat models are related to how one might define the **adversary’s assumptions, goals, and capabilities**.

  

These models are critical because they provide a systematic way to anticipate and mitigate attacks before they occur. 

---

**3. Cryptographic Building Blocks**

  

**Purpose of Cryptography:**

• Cryptography provides tools to secure communications over inherently insecure networks.

• It enables applications such as e-commerce, confidential messaging, digital identities, and more by ensuring that data remains private and untampered.

  

**Key Definitions:**

• **Encryption:** The process of converting plaintext into ciphertext so that only authorized parties can reverse the process.

• **Plaintext vs. Ciphertext:**

• _Plaintext_ is readable data.

• _Ciphertext_ is the obscured data resulting from encryption.

• **Cryptosystem:** A complete system that includes algorithms for encryption and decryption.

• **Cryptography vs. Cryptanalysis vs. Cryptology:**

• _Cryptography_ is about creating secure systems.

• _Cryptanalysis_ is about breaking those systems.

• _Cryptology_ encompasses both disciplines.

  

**Security Properties Enabled by Cryptography:**

• **Confidentiality:** Keeping information secret.

• **Integrity:** Ensuring that data is not altered during transmission or storage.

• **Authenticity:** Verifying the identity of the parties involved.

• Cryptography supports a wide range of applications, from digital signatures to secure key exchanges.

  

The lecture reinforces that while cryptography is a powerful tool, it is not a panacea—it must be correctly integrated into a larger security model. 

---

**4. Adversary Models in Applied Research**

  

**Role and Importance:**

• An **adversary model** is a formal representation of an attacker’s characteristics, including their assumptions (about resources and environment), goals (what data or control they seek), and capabilities (what actions they can take).

• In cryptography, such models underpin the security proofs of protocols. For example, the well-known **Dolev–Yao model** gives an attacker the power to intercept, send, and modify messages (essentially a man-in-the-middle).

  

**Evolution of Adversary Models:**

• Over time, adversary models have evolved from the basic Dolev–Yao model to more refined models such as the **Bellare–Rogaway model** and the **Canetti–Krawczyk (eCK) model**.

• These models introduce formalized **queries or capabilities** (like Send, Reveal, Corrupt, Execute) that quantify what an attacker might do in practice.

• The “Adversary model in applied research” paper reviews the use of these models beyond pure cryptography—extending into mobile and IoT security—emphasizing the need for clear definitions of adversary goals, assumptions, and capabilities.

  

**Adversary Model Components:**

• **Assumptions:** Define the attacker’s environment (external vs. internal, available tools, etc.).

• **Goals:** What the attacker aims to achieve (data exfiltration, protocol disruption, impersonation, etc.).

• **Capabilities:** Concrete actions the attacker can perform, such as intercepting messages, launching active attacks, or corrupting devices.

  

The paper argues that rigorous adversary models help researchers not only prove the security of protocols in theory but also compare and benchmark different security systems in practice. 

---

**5. Integration and Practical Implications**

  

**Interconnection of Concepts:**

• **Attacks and vulnerabilities** are understood better when seen through the lens of both threat and adversary models.

• **Security models** guide the design of systems by defining what must be protected and against whom.

• **Cryptographic building blocks** are used to enforce the desired security properties but must be implemented within a robust security framework.

  

**Practical Takeaways:**

• **System designers** should always start with a clear security model that includes an adversary model, ensuring that all potential attack vectors and surfaces are accounted for.

• **Cryptographic implementations** must be tested not only against theoretical adversaries but also with realistic threat models that mimic actual attacker behavior.

• **Ongoing research** in applied security—particularly in mobile and IoT domains—continues to refine these models to better address emerging threats, including physical attacks in cyber-physical systems.

---

**Summary**

  

Lecture 3 provides a comprehensive look at:

• **How attacks are defined, differentiated, and countered,** with specific emphasis on the methods (attack vectors) and the vulnerable points (attack surfaces) in a system.

• **The role of security and threat models** in structuring a coherent defense strategy.

• **The fundamental cryptographic concepts and components** that underpin secure communications.

• **The evolution and critical role of adversary models,** highlighting how formalizing an attacker’s assumptions, goals, and capabilities is key to both theoretical proofs and practical security solutions.

  

This integrated overview not only grounds you in the basic terminology and mechanisms of cryptography but also stresses the importance of precise and adaptable adversary models in modern applied security research.

---