# Windows Server Identity & Access Management

![Polarized Systems — Enterprise Network Architecture](images/enterprise-topology.png)

## Overview

**Identity and Access Management (IAM)** is a framework of policies, processes, and technologies used to manage digital identities and control access to enterprise systems, applications, and data. Through authentication, authorization, and access controls, IAM helps prevent unauthorized access, enforce security policies, and protect sensitive information.

Throughout these labs, we explore **Microsoft Active Directory and Group Policy Management** to administer user identities, manage permissions, and implement security policies within a Windows domain environment.

### Learning Outcomes

This section covers the following exercises:

- Exercise 1 – Password & Account Lockout Policies
- Exercise 2 – User Accounts & Groups
- Exercise 3 – Permissions & Access Controls
- Exercise 4 – Auditing
- Exercise 5 – Multifactor Authentication & Single Sign-On
- Exercise 6 – Data Security Concepts

After completing these exercises, you should be able to:

- Design and enforce password and account-lockout policies with Group Policy
- Create and manage Active Directory user accounts and account options
- Implement role-based access through security-group membership
- Apply least-privilege access with delegated administrative control
- Scope and apply Group Policy and force refresh with `gpupdate /force`
- Explain the multifactor-authentication factor model and OAuth-based single sign-on

---

## Lab Topology

![Lab Topology](images/lab-topology.png)

---

## Exercises

| # | Exercise | What I Did | Key Tools |
|---|----------|------------|-----------|
| 1 | [Password & Account Lockout Policies](exercise-1-password-and-account-lockout-policies/README.md) | Defined and enforced a domain-wide password and account-lockout policy through Group Policy, then scoped and applied it | Group Policy · Password Policy · Account Lockout Policy · `gpupdate` |
| 2 | [User Accounts & Groups](exercise-2-user-accounts-and-groups/README.md) | Created an Active Directory user, configured account options, and granted access through security-group membership | Active Directory Users and Computers · Security Groups |
| 3 | [Permissions & Access Controls](exercise-3-permissions-and-access-controls/README.md) | Delegated a scoped set of user-management rights with the Delegation of Control Wizard — least privilege in practice | Delegation of Control · AD DS |
| 4 | [Auditing](exercise-4-auditing/README.md) | Enabled object-level auditing and two advanced audit policies (account-logon and account-management) via Group Policy | Advanced Audit Policy · Object SACL auditing · Group Policy |
| 5 | [Multifactor Authentication & Single Sign-On](exercise-5-multifactor-authentication-and-single-sign-on/README.md) | Explained the authentication-factor model and OAuth-based single sign-on — the identity concepts that extend password security | MFA · SSO · OAuth |
| 6 | [Data Security Concepts](exercise-6-data-security-concepts/README.md) | Covered boot-level security, data storage and encryption (at rest / in transit, symmetric / asymmetric), and the risk-and-cost side of protecting data | BIOS/UEFI · Encryption · TLS / VPN · Risk management |

---

## Related Portfolios

- [Security Operations](https://github.com/PolarizedSystems/Security-Operations)
- [Vulnerability Management](https://github.com/PolarizedSystems/Vulnerability-Management)
- [Incident Response](https://github.com/PolarizedSystems/Cybersecurity-Incident-Response)
