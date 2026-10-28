# Exercise 5 – Multifactor Authentication & Single Sign-On

[← Back to Lab Overview](../README.md)

---

## Overview

**Multifactor Authentication (MFA)** and **Single Sign-On (SSO)** are essential components of modern Identity and Access Management (IAM). MFA strengthens account security by requiring multiple forms of identity verification, while SSO simplifies access by allowing users to authenticate once and access multiple applications.

In this exercise, I explored how these authentication technologies improve security and simplify access management across the environment.

**Key Learning Objectives:**

- **Multifactor Authentication (MFA):** Understand how additional authentication factors protect user accounts.
- **Single Sign-On (SSO):** Explore how centralized authentication simplifies access to multiple applications.
- **Identity Security:** Understand how MFA and SSO balance stronger security with user convenience.
This exercise builds foundational knowledge of enterprise authentication, identity protection, and access management.

---

## Multifactor Authentication (MFA)

Multifactor authentication verifies a user's identity by requiring **more than one independent proof** before granting access — so that compromising any single credential is not enough to get in. Instead of relying on a password alone, MFA combines proofs drawn from different categories, which generally fall into four buckets:

| Factor | "Something you…" | Examples |
|--------|------------------|----------|
| Knowledge | **know** | Password, PIN, security question |
| Possession | **have** | Smart card, hardware key fob, phone / authenticator app |
| Inherence | **are** | Fingerprint, facial recognition, retina scan |
| Behavior | **do** | Push-approval tap, CAPTCHA, typing pattern |

The strength comes from combining **different** categories — a password (*know*) plus a phone prompt (*have*), for instance. An attacker who phishes the password still can't produce the second factor, so the single most common path to compromise is closed off.

So much sensitive data now lives on personal computers and phones — banking, messages, contacts — that password-only protection simply doesn't hold up against modern, automated attacks. MFA is the practical, widely-adopted answer: a reliable way to protect accounts well beyond what any password can do on its own.

---

## Single Sign-On (SSO)

Single sign-on lets a user authenticate **once** and then reach many different services, websites, and applications without logging in again each time. Rather than remembering a separate credential for every system, the user maintains one trusted identity, and that identity is accepted across everything connected to it.

For organizations of any size, SSO streamlines the administration of credentials: accounts are managed in one place, access can be granted or revoked centrally, and users stop reusing weak passwords across a dozen systems just to cope with the sprawl.

A common framework behind modern SSO is **OAuth (Open Authorization)**. OAuth lets a third-party service access a user's data *without ever handling the user's password*. It works through an approved **access token**: the user consents, the token is issued, and OAuth acts as the mediator between the user and the service. When the user goes to open an application, the service contacts the identity provider, the provider validates the user, and access is granted — all without the password changing hands.

---


[← Previous: Exercise 4 – Auditing](../exercise-4-auditing/README.md) | [Back to Lab Overview](../README.md) | [Next: Exercise 6 – Data Security Concepts →](../exercise-6-data-security-concepts/README.md)
