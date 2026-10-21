# Exercise 5 – Multifactor Authentication & Single Sign-On

[← Back to Lab Overview](../README.md)

---

## Overview

Everything in the previous exercises strengthens a single factor: the password. But a password — however long or complex — is still one secret, and one secret can be stolen, phished, or guessed. This exercise looks at the two identity controls that address that limitation from opposite directions: **multifactor authentication**, which adds factors so a stolen password alone isn't enough, and **single sign-on**, which reduces the number of credentials a user has to juggle in the first place.

> 🔎 **Why this exercise is concept-focused.** The earlier exercises were hands-on configuration on the domain controller. This one is the knowledge capstone — multifactor authentication and single sign-on are architectural decisions that usually involve an identity provider, directory federation, or a cloud platform rather than a single server setting, so they're covered here as concepts to understand rather than a dialog box to click through. What follows is the reasoning a server administrator needs when these controls come up in design and in interviews.

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

> 🔎 **This connects to the smart-card MFA already in the portfolio.** In the Security Operations portfolio I enforced *smart-card-required* logon on an Active Directory account — a concrete, Windows-native implementation of the "something you have" factor. That exercise is MFA put into practice; this one is the framework that explains why it works and where it fits.

---

## Single Sign-On (SSO)

Single sign-on lets a user authenticate **once** and then reach many different services, websites, and applications without logging in again each time. Rather than remembering a separate credential for every system, the user maintains one trusted identity, and that identity is accepted across everything connected to it.

For organizations of any size, SSO streamlines the administration of credentials: accounts are managed in one place, access can be granted or revoked centrally, and users stop reusing weak passwords across a dozen systems just to cope with the sprawl.

A common framework behind modern SSO is **OAuth (Open Authorization)**. OAuth lets a third-party service access a user's data *without ever handling the user's password*. It works through an approved **access token**: the user consents, the token is issued, and OAuth acts as the mediator between the user and the service. When the user goes to open an application, the service contacts the identity provider, the provider validates the user, and access is granted — all without the password changing hands.

> 🔎 **MFA and SSO are complementary, not competing.** SSO concentrates access behind a single identity, which is convenient — but it also means that one login now unlocks many systems, raising the stakes of that login. That's exactly why SSO and MFA are deployed together: SSO reduces how many times a user authenticates, and MFA makes each of those authentications strong enough to be trusted with the keys to everything behind it.

---

> ### 🎤 Stakeholder Takeaway
>
> "These two controls pull in the same direction from opposite ends. Single sign-on means our people manage one strong identity instead of a dozen weak ones, which is easier for them and easier for us to govern. Multifactor authentication means that one identity can't be hijacked with a stolen password alone — an attacker would also need the user's phone, card, or fingerprint. Together they give us what every organization wants from identity: fewer passwords to go wrong, and far less damage when one does."

---

[← Previous: Exercise 4 – Auditing](../exercise-4-auditing/README.md) | [Back to Lab Overview](../README.md) | [Next: Exercise 6 – Data Security Concepts →](../exercise-6-data-security-concepts/README.md)
