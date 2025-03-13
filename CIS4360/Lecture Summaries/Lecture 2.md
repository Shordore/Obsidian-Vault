
**1. Cyber Systems and Their Components**

• **Definition of a Cyber System:**

A cyber system is any combination of hardware, software, protocols, people, procedures, and communications that work together to provide cyber services.

_Key Point:_ Security must be addressed across all these components.

---

**2. Understanding the Adversary**

  

**Who Wants to Attack Cyber Systems?**

• **Types of Attackers:**

• **Cybercriminals:** Individuals or groups seeking financial gain.

• **Cyberterrorists:** Groups with political or ideological motives, sometimes involving violence.

• **Spies:** Those engaging in espionage for strategic or competitive advantage.

• **End Users:** Sometimes insiders or users who inadvertently or deliberately cause security issues.

  

**The Adversary Model**

• **Concept:**

Every attacker (adversary) has different goals and capabilities. Security must be designed relative to:

1. **Desired Security Properties:** What the system must protect (e.g., confidentiality, integrity, availability).

2. **Adversary Capabilities:** The tools, methods, and resources available to the attacker.

• **Formalization:**

An adversary model specifies an attacker’s objectives and limitations, forming the basis for evaluating and designing defenses.

---

**3. Security Properties and What They Mean**

  

**Core Security Goals**

• **Confidentiality:**

Ensuring that sensitive information is accessible only to those with authorized access.

_Example:_ Encrypting communication between Alice and Bob to prevent eavesdropping by Eve.

• **Integrity:**

Ensuring that data remains accurate and unaltered during storage, transmission, or processing.

_Example:_ Using hash functions or digital signatures to detect tampering.

• **Availability:**

Ensuring that systems and data are accessible to authorized users when needed.

_Example:_ Implementing redundancy and failover systems to maintain service uptime.

  

**Additional Security Properties**

• **Authentication:**

Verifying the identity of a user or system (e.g., proving “you are who you say you are”).

• **Authorization:**

Granting access rights or privileges based on authenticated identities.

• **Anonymity:**

Concealing the identity of the sender while allowing communication (e.g., sending messages anonymously).

• **Client and Server Authentication:**

Both the client (Alice) and the service (Bob’s server) must prove their identities to each other to establish trust.

---

**4. Defining “Security”**

  

**Different Perspectives on Security**

• **Statements About Security:**

Claims like “This computer is secure” or “The network is secure” are not inherently credible without context.

• **Formal Definitions:**

• **Garfinkel and Spafford (1991):**

A computer is secure if you can depend on it and its software to behave as expected.

• **Harrison, Ruzzo, Ullman (1978):**

Security involves preventing access by unauthorized users.

  

_Key Insight:_ Security is relative—it depends on the policies, the defined assets, and the adversary model in place.

---

**5. Security Policy**

• **Purpose:**

A security policy provides the rules and design intent for protecting assets. It specifies:

• Which assets need protection.

• Who is authorized to access them.

• How access is allowed or denied.

• **Formal Policy Characteristics:**

Defines authorized versus unauthorized states and how transitions between these states occur.

---

**6. Threats, Vulnerabilities, and Risk**

  

**Threats and Vulnerabilities**

• **Threat:**

Any combination of circumstances and entities inclined to harm assets or cause security violations.

• **Vulnerability:**

A weakness or flaw in a system (due to bad software, poor design, misconfiguration, etc.) that can be exploited by a threat.

  

**Risk Assessment**

• **Risk Definition:**

The potential for an asset to be misused, often modeled as:

**Risk (R) = Threat (T) × Vulnerability (V) × Asset Value (C)**

• **Considerations:**

• Quantifying threat likelihood and impact.

• Dealing with unknown vulnerabilities (e.g., zero-days).

• Balancing the cost of protection against the potential damage.

---

**7. Types of Attacks**

• **Passive Attacks:**

Involve eavesdropping or monitoring without altering system resources (e.g., network sniffing).

• **Active Attacks:**

Involve deliberate actions like tampering, password guessing, or modifying data.

• **Spoofing:**

Impersonating another entity to gain unauthorized access.

• **Denial of Service (DoS):**

Preventing legitimate users from accessing resources, either by overwhelming the system or blocking network traffic.

• **Compromise:**

Occurs when an attack is successful, often resulting in the attacker taking control or altering resources.

---

**8. Trust and Trust Models**

• **Trust:**

The degree to which an entity is expected to act in a reliable or secure manner (e.g., not exposing user passwords).

• **Trust vs. Trustworthy:**

• **Trusted:** A system or component that, if it fails, can break the security policy.

• **Trustworthy:** A trusted component that is reliably secure and does not fail.

• **Trust Models:**

Frameworks that define who is trusted to do what within a system. They help determine the necessary security measures based on the roles and behaviors of different entities.

---

**Summary**

  

Lecture 2 lays a comprehensive foundation for understanding security by:

• Defining what constitutes a cyber system.

• Identifying various types of attackers and the importance of modeling adversary behavior.

• Establishing the critical security properties (confidentiality, integrity, availability, and more) and what they mean in practice.

• Discussing how security is relative and defined by policies.

• Exploring risk assessment, vulnerabilities, and the nature of different attacks.

• Introducing the concept of trust and how trust models influence security design.

  

This detailed breakdown provides you with a roadmap for understanding how these fundamental concepts interplay to form a secure cyber system. Revisiting these concepts and considering real-world examples will strengthen your grasp of computer and information security principles.

---

_Reference:_