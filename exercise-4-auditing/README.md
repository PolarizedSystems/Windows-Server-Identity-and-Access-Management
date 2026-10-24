# Exercise 4 – Auditing

[← Back to Lab Overview](../README.md)

---

## Overview

**Security auditing** is the process of monitoring and recording user activity, login attempts, and system changes to identify suspicious behavior and maintain accountability. Within **Active Directory**, auditing helps administrators track access to network resources and detect potential security violations.

In this exercise, I explore **Windows security auditing** to monitor user activity and strengthen visibility across the domain.

**Key Configuration Activities:**

- **User Activity:** Monitor and review account-related security events.
- **Login Auditing:** Track successful and failed authentication attempts.
- **Group Membership:** Audit changes to security group memberships.
- **Security Logs:** Review recorded events to investigate potential security issues.

This exercise demonstrates practical experience in Windows security auditing, access monitoring, and enterprise security operations.

## Device

- **corp-dc-001** – Windows Server – Domain Controller / Active Directory & Group Policy (192.168.20.2)

---

## Task 1 – Enable Object-Level Auditing on the Users Container

1. In Active Directory Users and Computers, locate the **Users** container.

   ![Users container](screenshots/exercise-4/e4-01-aduc-users-container.png)

2. Turn on **View → Advanced Features** so object security and auditing tabs are visible.

   ![Enable advanced features](screenshots/exercise-4/e4-02-enable-advanced-features.png)

3. Open the **Users** container's **Properties**.

   ![Open Users properties](screenshots/exercise-4/e4-03-open-users-properties.png)

4. Go to the **Security** tab.

   ![Security tab](screenshots/exercise-4/e4-04-users-security-tab.png)

5. Click **Advanced** to reach the auditing settings.

   ![Security – advanced](screenshots/exercise-4/e4-05-security-advanced.png)

6. On the **Auditing** tab, click **Add** to create an audit entry.

   ![Auditing tab – add](screenshots/exercise-4/e4-06-auditing-tab-add.png)

7. Click **Select a principal** to choose who the audit entry applies to.

   ![Select auditing principal](screenshots/exercise-4/e4-07-select-auditing-principal.png)

8. Select **Ron Simmons**.

   ![Select Ron Simmons](screenshots/exercise-4/e4-08-select-ron-simmons.png)

9. Set the **Type** to **All** so both successful and failed access is recorded.

   ![Auditing entry – type all](screenshots/exercise-4/e4-09-auditing-entry-type-all.png)

10. Review the permissions the audit entry will track.

    ![Auditing entry – permissions](screenshots/exercise-4/e4-10-auditing-entry-permissions.png)

11. The auditing entries are configured on the container.

    ![Auditing entries configured](screenshots/exercise-4/e4-11-auditing-entries-configured.png)

12. Confirm the advanced security settings.

    ![Confirm security settings](screenshots/exercise-4/e4-12-confirm-security-settings.png)

13. Close Active Directory Users and Computers.

    ![Close ADUC](screenshots/exercise-4/e4-13-close-aduc.png)

---

## Task 2 – Create the Account-Logon Audit Policy

14. Open **Group Policy Management**.

    ![Open Group Policy Management](screenshots/exercise-4/e4-14-open-group-policy-management.png)

15. Create a new GPO.

    ![Create audit GPO](screenshots/exercise-4/e4-15-create-audit-gpo.png)

16. Name it **Password Audit**.

    ![Name GPO – Password Audit](screenshots/exercise-4/e4-16-name-gpo-password-audit.png)

17. Edit the GPO.

    ![Edit Password Audit GPO](screenshots/exercise-4/e4-17-edit-password-audit-gpo.png)

18. Navigate to **Computer Configuration → Policies → Windows Settings → Security Settings → Advanced Audit Policy Configuration → Account Logon**.

    ![Navigate to Account Logon audit](screenshots/exercise-4/e4-18-navigate-account-logon-audit.png)

19. Open **Audit Credential Validation**.

    ![Select credential validation](screenshots/exercise-4/e4-19-select-credential-validation.png)

20. Configure it to audit both **Success** and **Failure**.

    ![Audit credential validation](screenshots/exercise-4/e4-20-audit-credential-validation.png)

21. The Explain tab notes that credential validation events are where logon-password checks are recorded — the heart of logon auditing.

    ![Credential validation – explanation](screenshots/exercise-4/e4-21-credential-validation-explain.png)

22. Back in the Account Logon list.

    ![Account logon audit list](screenshots/exercise-4/e4-22-account-logon-audit-list.png)

23. Configure **Audit Kerberos Authentication Service** (Success and Failure).

    ![Audit Kerberos authentication](screenshots/exercise-4/e4-23-audit-kerberos-authentication.png)

24. The Explain tab describes Kerberos ticket-granting activity.

    ![Kerberos authentication – explanation](screenshots/exercise-4/e4-24-kerberos-authentication-explain.png)

25. Open **Audit Kerberos Service Ticket Operations**.

    ![Select Kerberos service ticket](screenshots/exercise-4/e4-25-select-kerberos-service-ticket.png)

26. The Explain tab covers service-ticket requests.

    ![Kerberos service ticket – explanation](screenshots/exercise-4/e4-26-kerberos-service-ticket-explain.png)

27. Configure it for Success and Failure.

    ![Audit Kerberos service ticket](screenshots/exercise-4/e4-27-audit-kerberos-service-ticket.png)

28. Configure **Audit Other Account Logon Events**.

    ![Audit other account logon](screenshots/exercise-4/e4-28-audit-other-account-logon.png)

29. The Explain tab describes the remaining logon-related events.

    ![Other account logon – explanation](screenshots/exercise-4/e4-29-other-account-logon-explain.png)

30. The Account Logon audit policy is fully configured.

    ![Account logon audit configured](screenshots/exercise-4/e4-30-account-logon-audit-configured.png)

> 🔎 **Why Kerberos auditing matters in a domain.** In Active Directory, authentication runs on Kerberos — the domain controller issues tickets that prove identity. Auditing ticket-granting and service-ticket activity is how you catch abnormal authentication: tickets requested for accounts that shouldn't be active, or the telltale patterns of ticket-based attacks. It's logon visibility at the protocol level, not just the login prompt.

---

## Task 3 – Create the Account-Management Audit Policy

31. Create another new GPO.

    ![Create group audit GPO](screenshots/exercise-4/e4-31-create-group-audit-gpo.png)

32. Name it **Group Audit**.

    ![Name GPO – Group Audit](screenshots/exercise-4/e4-32-name-gpo-group-audit.png)

33. Edit the GPO.

    ![Edit Group Audit GPO](screenshots/exercise-4/e4-33-edit-group-audit-gpo.png)

34. Navigate to **Advanced Audit Policy Configuration → Account Management**.

    ![Navigate to Account Management audit](screenshots/exercise-4/e4-34-navigate-account-management-audit.png)

35. Open **Audit Application Group Management**.

    ![Select application group management](screenshots/exercise-4/e4-35-select-application-group-management.png)

36. Configure it for Success and Failure.

    ![Audit application group management](screenshots/exercise-4/e4-36-audit-application-group-management.png)

37. The Explain tab describes application-group changes.

    ![Application group management – explanation](screenshots/exercise-4/e4-37-application-group-management-explain.png)

38. Open **Audit Computer Account Management**.

    ![Select computer account management](screenshots/exercise-4/e4-38-select-computer-account-management.png)

39. Configure it for Success and Failure.

    ![Audit computer account management](screenshots/exercise-4/e4-39-audit-computer-account-management.png)

40. The Explain tab describes computer-account changes.

    ![Computer account management – explanation](screenshots/exercise-4/e4-40-computer-account-management-explain.png)

41. Open **Audit Distribution Group Management**.

    ![Select distribution group management](screenshots/exercise-4/e4-41-select-distribution-group-management.png)

42. Configure it for Success and Failure.

    ![Audit distribution group management](screenshots/exercise-4/e4-42-audit-distribution-group-management.png)

43. The Explain tab describes distribution-group changes.

    ![Distribution group management – explanation](screenshots/exercise-4/e4-43-distribution-group-management-explain.png)

44. Open **Audit Other Account Management Events**.

    ![Select other account management](screenshots/exercise-4/e4-44-select-other-account-management.png)

45. Configure it for Success and Failure.

    ![Audit other account management](screenshots/exercise-4/e4-45-audit-other-account-management.png)

46. The Explain tab describes the remaining account-management events (including password-hash access).

    ![Other account management – explanation](screenshots/exercise-4/e4-46-other-account-management-explain.png)

47. Configure **Audit Security Group Management** for Success and Failure.

    ![Audit security group management](screenshots/exercise-4/e4-47-audit-security-group-management.png)

48. The Explain tab describes security-group changes — the events that track privilege grants.

    ![Security group management – explanation](screenshots/exercise-4/e4-48-security-group-management-explain.png)

49. Security Group Management is now set in the policy list.

    ![Security group management set](screenshots/exercise-4/e4-49-security-group-management-set.png)

50. Configure **Audit User Account Management** for Success and Failure.

    ![Audit user account management](screenshots/exercise-4/e4-50-audit-user-account-management.png)

51. The Explain tab describes user-account changes — creation, deletion, enable/disable, password resets.

    ![User account management – explanation](screenshots/exercise-4/e4-51-user-account-management-explain.png)

52. The Account Management audit policy is fully configured.

    ![Account management audit configured](screenshots/exercise-4/e4-52-account-management-audit-configured.png)

> 🔎 **Account-management auditing is how you catch privilege abuse.** The single most important event to watch in a domain is a change to **security group membership** — because adding an account to a privileged group is exactly how an attacker escalates and how insider misuse happens. Auditing user- and group-management events means every one of those changes leaves a record naming who did it and when. This ties directly back to the detection work in the Security Operations portfolio, where Events 4728/4737 (group changes) were hunted from the collected logs.

---

> ### 🎤 Stakeholder Takeaway
>
> "We now have a record of who signs in, who fails to, and who changes accounts and group memberships across the domain. If an account is brute-forced, if someone is quietly added to an admin group, or if a password is reset without authorization, it leaves a trail we can follow. Auditing doesn't stop an attack on its own — but it's what turns a vague suspicion into a clear timeline, and it's the difference between knowing what happened and only guessing. Fed into our SIEM, these events become live alerts rather than after-the-fact forensics."

---

[← Previous: Exercise 3 – Permissions & Access Controls](../exercise-3-permissions-and-access-controls/README.md) | [Back to Lab Overview](../README.md) | [Next: Exercise 5 – Multifactor Authentication & Single Sign-On →](../exercise-5-multifactor-authentication-and-single-sign-on/README.md)
