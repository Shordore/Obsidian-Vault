
**1. Overview of Passwords in Authentication**

• **Role of Passwords:**

Passwords are a primary form of “something you know” used in authentication. They allow users to prove their identity when accessing systems and services.

• **Key Function:**

They serve as secret credentials that, when verified, grant access to resources and secure communications.

---

**2. Design Challenges for Password Systems**

• **Usability vs. Security:**

• **Memorability:** A password should be easy for users to remember.

• **Strength:** At the same time, it must be hard for attackers to guess, either through brute-force, dictionary attacks, or other methods.

• **Key Questions:**

• What constitutes a “good” password?

• How should passwords be stored (and in what form) to minimize risk if the storage is compromised?

• How is the knowledge of the password verified without exposing it?

---

**3. Secure Password Storage**

• **Storing Plaintext Passwords:**

Storing passwords in plaintext is extremely insecure, as compromising the storage (e.g., a stolen database) directly exposes every password.

• **One-Way Functions and Hashing:**

• **Hashing:** Instead of storing passwords directly, systems should store the output of a one-way hash function applied to the password.

• **Verification:** When a user logs in, the system hashes the provided password and compares it to the stored hash.

• **Salting:**

• **Definition:** A salt is a random value added to the password before hashing.

• **Benefits:**

• Ensures that identical passwords yield different hashes across users.

• Makes precomputed attacks (like rainbow table attacks) infeasible.

• **Implementation Example:**

• UNIX systems often prepend a two-character salt to the password, resulting in unique hash values even for users with the same password.

---

**4. Attacks on Passwords**

• **Brute-Force Attacks:**

• Attackers try every possible combination until the correct password is found.

• The time required depends on the password’s length and complexity.

• **Dictionary Attacks:**

• Use precompiled lists of common words, phrases, and known password patterns.

• Attackers prioritize these likely guesses, significantly reducing the search space compared to brute force.

• **Precomputed Attacks (Rainbow Tables):**

• Attackers precompute the hashes of large dictionaries of potential passwords to quickly find matches.

• **Countermeasure:** Salting passwords disrupts the effectiveness of rainbow tables because each password gets a unique salt, meaning a separate table would be needed for each salt value.

• **Offline Attacks:**

• Once an attacker gains access to a password file (e.g., through a system breach), they can perform dictionary or brute-force attacks without interacting with the live system, often using powerful hardware like GPUs.

---

**5. Password Policies and User Behavior**

• **Password Complexity Requirements:**

• Policies may require a mix of uppercase and lowercase letters, numbers, and special characters.

• Such requirements aim to increase the entropy of passwords, making them less predictable.

• **Password Change Policies:**

• Some organizations enforce periodic password changes.

• **Debate:** Frequent changes can sometimes lead to weaker passwords if users choose simple, incremental variations or write them down.

• **The “Magical Number Seven, Plus or Minus Two”:**

• Cognitive psychology suggests that humans can only remember around 7 (±2) pieces of information, which limits the length and complexity of a password that a user can reliably remember.

---

**6. Countermeasures and Enhancements**

• **Password Managers:**

• Tools that generate and store complex, unique passwords for different accounts.

• They help users overcome the limitations of human memory and reduce the risk of password reuse across sites.

• **Multifactor Authentication (MFA):**

• Combines passwords with additional authentication factors, such as something you have (e.g., a token or smartphone app) or something you are (e.g., biometrics), to enhance overall security.

• MFA can mitigate risks if a password is compromised.

---

**7. Practical Implications**

• **Balancing Usability and Security:**

• Systems must find the right balance to ensure passwords are both secure and user-friendly.

• **Implementation Considerations:**

• Use of strong one-way hash functions combined with unique salts is critical.

• Policies should be designed to discourage weak or reused passwords while considering user convenience.

• **Ongoing Challenges:**

• Attackers continually develop faster hardware and more sophisticated cracking methods, so systems must regularly update their security measures.

• Educating users about creating strong, memorable passwords and the benefits of password managers and MFA is essential.

---

**Summary**

  

Lecture 14 delves into the complexities and challenges of password-based authentication. It explains that while passwords are a cornerstone of digital identity, their effectiveness depends on both technical implementations (secure storage using hashing and salting) and the human factors associated with password creation and management. The lecture covers common attack methods—such as brute-force, dictionary, and rainbow table attacks—and emphasizes the need for robust countermeasures like password policies, password managers, and multifactor authentication to mitigate these risks.

---

_Reference:_