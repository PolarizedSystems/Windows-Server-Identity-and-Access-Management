# Exercise 6 – Data Security Concepts

[← Back to Lab Overview](../README.md)

---

## Overview

Controlling *who* can access a system is only half the job; the other half is protecting the *data* itself — before the operating system even loads, while it sits at rest, and as it travels across the network. This exercise rounds out the lab by looking at data security from the ground up: securing the boot process, choosing where and how data is stored and encrypted, and weighing the cost of protecting data against the risk of losing it.

---

## 1. Boot-Level Security: BIOS, UEFI & the Bootloader

One of the most overlooked moments of vulnerability is the one before the operating system even starts. When a machine powers on, its firmware — the legacy **BIOS** or its modern replacement, **UEFI** — runs the Power-On Self-Test, checks the attached hardware, and hands off to the bootloader that starts the OS. Anyone who can reach that firmware menu can change the boot order, disable security features, or boot from their own media.

Setting a **BIOS/UEFI password** closes that door: it stops an unauthorized person from altering firmware settings or booting the machine from an external drive. A separate **bootloader password** adds another layer, blocking tricks like dropping into single-user mode to reset the root password. Both should be set as early as possible in a server's life.

---

## 2. Data Storage & Encryption

### Where data lives: on-site vs. off-site

Some data has to stay on the premises — **PII** (personally identifiable information), **PHI** (protected health information), and data covered by **PCI DSS** (cardholder data) are the common examples, and how long each is kept is dictated by regulation and company policy.

- **On-site storage** keeps data close to the primary system on local disks or tape, which makes access and restoration fast — but a single fire or flood can take the data and its backups together.
- **Off-site storage** places copies in a separate facility or the cloud, retrievable from anywhere with a connection, so a local catastrophe doesn't become a total loss. The trade-off is trusting a provider and managing that relationship.

Most organizations use both, keeping the most sensitive data under their own control while using off-site copies for resilience.

### Encryption: data at rest and data in transit

- **Data at rest** is stored data not currently in use — the live copy plus every backup and archive. Full-drive encryption with tools like **BitLocker** (or EFS, VeraCrypt, File Vault) keeps it unreadable if a disk is removed or stolen. The general rule: encrypt the whole drive rather than one file at a time, so nothing sensitive is accidentally left in the clear. This protects the data's **confidentiality, integrity, and authenticity**.
- **Data in transit** is data moving between systems. Left unprotected, many protocols send it in clear text — plain **HTTP** on port 80 is readable by anyone sniffing the wire. Adding **SSL/TLS** turns it into **HTTPS** on port 443, defeating sniffing, man-in-the-middle, and eavesdropping. A **VPN** extends the same idea to all traffic, wrapping it in an encrypted tunnel across the public internet.

### Encryption algorithms: symmetric vs. asymmetric

| | Symmetric (secret-key) | Asymmetric (public-key / PKI) |
|---|---|---|
| **Keys** | One shared key encrypts and decrypts | A public/private key pair plus a certificate |
| **Speed** | Fast, low processing overhead | Slower, more computationally expensive |
| **Challenge** | Getting the shared key to the other party safely | Managing keys and certificates |
| **Example** | AES (128/192/256-bit) | Public Key Infrastructure, digital signatures |

In practice the two are combined: asymmetric encryption safely delivers the shared key, then fast symmetric encryption handles the bulk of the data. Asymmetric cryptography also underpins **digital signatures** — proving who sent something and supporting **non-repudiation** — and is the basis of the **SSL/TLS certificates** issued by a certificate authority. Its one hard rule: lose the private key and the data can't be recovered.

---

## 3. The Business Impact of Data Security

### Data value prioritization

Not all data is equally valuable, so the first step is assessing each data type: how important it is, how many copies are needed, where it must be stored, and — just as importantly — what can be safely discarded. Knowing what *not* to keep saves real money in storage and shrinks the attack surface.

### Data lifecycle management

Every piece of data moves through five phases, from the moment it's created to the moment it's destroyed:

1. **Production** – the data is created or captured
2. **Storage** – it's saved, in a format and location chosen for its sensitivity
3. **Utilization** – it's used in business activities
4. **Archiving** – it's retained but no longer in active use
5. **Disposal** – it's securely destroyed when no longer needed

Managing data across this lifecycle is what keeps retention deliberate rather than accidental.

### The cost of security versus risk

Security spending is ultimately a balance against risk, and there are four standard ways to handle any given risk:

- **Avoidance** – drop the risky activity entirely (e.g., stop using an exposed program)
- **Acceptance** – knowingly accept a low-likelihood or low-impact risk
- **Mitigation** – reduce the risk with controls like firewalls and intrusion prevention
- **Transference** – shift the risk to someone else, such as cyber-insurance or a managed provider
- 
The right choice weighs the cost of the safeguard against the potential loss — and a data breach's cost is rarely just the cleanup. It includes reputational damage and regulatory fines, which is exactly why security is treated as a business investment, not just an IT expense.
---

[← Previous: Exercise 5 – Multifactor Authentication & Single Sign-On](../exercise-5-multifactor-authentication-and-single-sign-on/README.md) | [Back to Lab Overview](../README.md)
