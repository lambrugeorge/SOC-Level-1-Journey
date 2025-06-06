# Unified Kill Chain (UKC)

Understanding the behaviors, objectives, and methodologies of a cyber threat is a vital step in establishing a strong cybersecurity defense (known as a cybersecurity posture).

In this room, you will be introduced to the **Unified Kill Chain (UKC)** framework, which is used to help understand how cyberattacks occur.

![Unified Kill Chain Overview](1.png)

## Learning Objectives

- Understand why frameworks such as the UKC are important and helpful in establishing a good cybersecurity posture.
- Use the UKC to understand an attacker's motivation, methodologies, and tactics.
- Learn about the various phases of the UKC.
- Discover how the UKC complements other frameworks, such as MITRE.

---

## What is a "Kill Chain"?

Originating from the military, a **“Kill Chain”** is a term used to explain the various stages of an attack. In cybersecurity, it describes the methodology or path attackers (e.g., hackers or APTs) use to approach and intrude on a target.

![Kill Chain Example](2.png)

For example, an attacker scanning, exploiting a web vulnerability, and escalating privileges constitutes a **Kill Chain**. We will explore these stages in greater detail later in this room.

The objective is to understand an attacker's **Kill Chain** so that defensive measures can be implemented to either preemptively protect a system or disrupt an attacker's attempt.

### Question: Where does the term "Kill Chain" originate from?

**Answer:** The **military**.

---

## Threat Modeling in Cybersecurity

**Threat modeling** is a series of steps aimed at improving the security of a system. It involves identifying risks and can be summarized as follows:

![Threat Modeling Process](3.png)

1. **Identify critical systems and applications**: Determine what needs to be secured and its function in the environment. For example, is the system critical to operations, or does it hold sensitive information like payment data or addresses?
2. **Assess vulnerabilities**: Identify weaknesses in these systems and how they could potentially be exploited.
3. **Create a mitigation plan**: Develop a plan to secure these systems and address the identified vulnerabilities.
4. **Implement preventive policies**: Establish measures to prevent vulnerabilities from reoccurring, such as adopting a secure software development life cycle (SDLC) or training employees on phishing awareness.

Threat modeling is crucial for reducing risks within a system or application. It provides a high-level overview of an organization’s IT assets (an **asset** in IT refers to a piece of software or hardware) and outlines procedures to resolve vulnerabilities.

The UKC framework supports threat modeling by identifying potential attack surfaces and how these systems may be exploited.

### Additional Frameworks for Threat Modeling

- **STRIDE**
- **DREAD**
- **CVSS**

If you are interested in learning more, check out the **“Principles of Security”** room on TryHackMe.

### Question: What is the technical term for a piece of software or hardware in IT?

**Answer:** **Asset**

---

## Next Steps

In the next task, we will dive deeper into the **Unified Kill Chain** framework and its phases.
