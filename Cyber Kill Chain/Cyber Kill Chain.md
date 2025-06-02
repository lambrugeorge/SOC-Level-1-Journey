# Cyber Kill Chain 🚀

![Cyber Kill Chain Diagram](1.png)

The **Cyber Kill Chain** is a concept adapted from military strategy, describing the stages of a cyber attack. Developed by Lockheed Martin in 2011, this framework helps cybersecurity professionals understand and defend against threats by breaking down an attack into distinct phases.

Understanding the Cyber Kill Chain is crucial for anyone in cybersecurity, including SOC Analysts, Security Researchers, Threat Hunters, and Incident Responders. By recognizing each phase, you can spot intrusion attempts early and disrupt the attack before it causes damage. 🛡️

## Why Learn the Cyber Kill Chain? 🤔

- **Identify Security Gaps:** Assess your network and systems to find and fix vulnerabilities.
- **Defend Against Attacks:** Protect against ransomware, data breaches, and Advanced Persistent Threats (APTs).
- **Understand Adversaries:** Learn how attackers think and operate to better defend your organization.

## The 7 Phases of the Cyber Kill Chain

1. **Reconnaissance**
2. **Weaponization**
3. **Delivery**
4. **Exploitation**
5. **Installation**
6. **Command & Control**
7. **Actions on Objectives**

In this room, you'll learn about each phase, the pros and cons of the traditional Cyber Kill Chain, and how to break the chain to stop attackers in their tracks. 🛑

---

## Phase 1: Reconnaissance 🔍

To defend against attacks, it's important to understand how attackers gather information. **Reconnaissance** is the planning phase, where adversaries collect data about their target.

![Reconnaissance](2.png)

### What is OSINT? 🌐

**OSINT (Open-Source Intelligence)** is a key part of reconnaissance. Attackers use publicly available information—like company size, employee emails, and phone numbers—to identify potential targets.

> Learn more about OSINT in the Varonis article: ["What is OSINT?"](https://www.varonis.com/blog/what-is-osint)

### Attacker's Perspective

Imagine an attacker named "Megatron" planning a sophisticated attack. His first step is reconnaissance, using OSINT to gather as much information as possible.

#### Example: Email Harvesting 📧

Email harvesting involves collecting email addresses from public sources. Attackers use these for phishing—tricking victims into revealing sensitive information.

**Popular Reconnaissance Tools:**
- `theHarvester`: Gathers emails, names, subdomains, IPs, and URLs from public sources.
- `Hunter.io`: Finds contact information linked to a domain.
- `OSINT Framework`: A collection of OSINT tools organized by category.

Attackers also use social media platforms like LinkedIn, Facebook, Twitter, and Instagram to gather information about companies and individuals. This data can be used to craft convincing phishing attacks. 🕵️‍♂️

---

**Learning Outcome:**  
By the end of this room, you'll be able to recognize each phase of the Cyber Kill Chain and know how to disrupt an attack before it succeeds. Let's continue exploring the next phases! 🚦



## Phase 3: Weaponization 🔍

## What I Learned Today 💡
![Weaponization](3.png)

Today I dove into **Task 3: Weaponization** and discovered how attackers craft and deliver their "weapons" after a successful recon phase. Here's a summary of what I learned and reflected on:

### 🔍 Key Concepts

- **Malware** – Malicious software meant to disrupt, damage, or gain unauthorized access.  
- **Exploit** – Code that takes advantage of a vulnerability.  
- **Payload** – The part of the attack that actually executes malicious actions.

### 🎯 The Attacker’s Strategy

Our fictional attacker **"Megatron"** prefers not to get his hands dirty and instead:

- Buys a **ready-made payload** from the Dark Web 🕵️‍♂️
- Uses Microsoft Office files with **malicious macros** to trick users 📄
- Might also plant USB drives loaded with malware 🖲️
- Chooses **C2 (Command & Control)** techniques for persistence 🔄
- Installs **backdoors** to regain access whenever he wants 🔓

### 🧠 Personal Reflection

Understanding this phase helped me see how important **prevention** is — not just detection. It made me appreciate how even simple tools like Office documents 📎 can become dangerous if misused.

Also, it reinforced how **automation (macros/VBA)** can be powerful — both for good and for evil. It's up to us to know the difference and stay one step ahead! 👣

### ❓Knowledge Check

> This term is referred to as a group of commands that perform a specific task. You can think of them as subroutines or functions that contain the code that most users use to automate routine tasks. But malicious actors tend to use them for malicious purposes and include them in Microsoft Office documents.  
> **Answer:** `Macros` ✅

---

🔐 On to the next phase in the cyber kill chain! Stay curious & stay safe! 🌐

## Phase 4: Delivery 🚚

![Delivery](4.png)

The **Delivery** phase is when "Megatron" selects how to transmit the payload or malware to the target. Attackers have several creative options at their disposal:

- **Phishing Email 🎣:** After reconnaissance, the attacker crafts a malicious email targeting either a specific person (**spearphishing**) or multiple people in the company. The email contains the payload or malware. For example, "Megatron" notices that Nancy from Sales at Company A often likes LinkedIn posts from Scott, a Service Delivery Manager at Company B. Guessing they communicate via work email, "Megatron" creates a convincing email using Scott’s name and a lookalike domain, then sends Nancy a fake "Invoice" containing the payload.

- **Infected USB Drives 💾:** Attackers may distribute USB drives in public places like coffee shops, parking lots, or even mail them directly to companies. Sometimes, they print the company’s logo on the drives and pretend to be a customer sending a "gift." If someone plugs in the USB, malware is delivered. [Read about a real attack like this on CSO Online.](https://www.csoonline.com/article/3642217/cybercriminal-group-mails-malicious-usb-dongles-to-targeted-companies.html)

- **Watering Hole Attack 🕳️:** Here, attackers compromise a website frequently visited by the target group. Victims are lured (often via "harmless" emails) to visit the site, which secretly redirects them to a malicious page. Visiting the site can trigger a **drive-by download**—malware is installed without the victim’s knowledge. For example, a fake browser extension pop-up may appear, tricking users into downloading malware.

---

**Key Takeaway:**  
Attackers use social engineering, technical tricks, and creativity to deliver their payloads. Recognizing these delivery methods is crucial for defending your organization! 🛡️

