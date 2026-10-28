# Exercise 1 – Password & Account Lockout Policies

[← Back to Lab Overview](../README.md)

---

## Overview

**Password and account lockout policies** are essential security controls that protect enterprise systems against unauthorized access and password-guessing attacks. Properly configured policies help balance strong account security with user accessibility.

 **In this exercise, we'll look at configuring **Active Directory password and account lockout policies** using Windows Group Policy Management.**

## Objectives

- **Password Policies:** Define password complexity, length, and expiration requirements.
- **Account Lockout:** Configure failed-login thresholds and account lockout settings.
- **Group Policy Management:** Apply security policies across the Windows domain.
- **Policy Enforcement:** Update Group Policy to apply the configured settings.


## Device

- **corp-dc-001** – Windows Server – Domain Controller / Active Directory & Group Policy (192.168.20.2)

---

## Task 1 – Create the Password Policy GPO

1. Log into **corp-dc-001** as the domain administrator.

   ![Log into the domain controller](screenshots/exercise-1/e1-01-login-domain-controller.png)

2. Open **Server Manager → Tools → Group Policy Management**.

   ![Open Group Policy Management](screenshots/exercise-1/e1-02-open-group-policy-management.png)

3. Right-click the domain and choose **Create a GPO in this domain, and link it here**.

   ![Create a GPO](screenshots/exercise-1/e1-03-create-gpo.png)

4. Name the new GPO **Password Policy**.

   ![Name the GPO](screenshots/exercise-1/e1-04-name-gpo-password-policy.png)

5. Right-click the new GPO and choose **Edit** to open the Group Policy Management Editor.

   ![Edit the GPO](screenshots/exercise-1/e1-05-edit-password-policy-gpo.png)

6. Navigate to **Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy**.

   ![Navigate to Password Policy](screenshots/exercise-1/e1-06-navigate-password-policy.png)

7. The password policy settings are listed, all currently undefined.

   ![Password policy settings](screenshots/exercise-1/e1-07-password-policy-settings.png)

---

## Task 2 – Configure the Password Policy

8. **Enforce password history** — set it to remember **5** previous passwords so users can't immediately reuse an old one.

   ![Enforce password history](screenshots/exercise-1/e1-08-enforce-password-history.png)

9. The Explain tab describes how password history prevents continual reuse of old passwords.

   ![Enforce password history – explanation](screenshots/exercise-1/e1-09-enforce-password-history-explain.png)

10. Back in the policy list.

    ![Policy list](screenshots/exercise-1/e1-10-password-policy-list.png)

11. **Maximum password age** — set to **60 days**, forcing a periodic password change.

    ![Maximum password age](screenshots/exercise-1/e1-11-maximum-password-age.png)

12. The Explain tab notes the security value of rotating passwords on a schedule.

    ![Maximum password age – explanation](screenshots/exercise-1/e1-12-maximum-password-age-explain.png)

13. Back in the policy list.

    ![Policy list](screenshots/exercise-1/e1-13-password-policy-list-2.png)

14. **Minimum password age** — the Explain tab describes how a minimum age stops users from cycling rapidly through passwords to defeat history enforcement.

    ![Minimum password age – explanation](screenshots/exercise-1/e1-14-minimum-password-age-explain.png)

15. Open **Minimum password length**.

    ![Minimum password length](screenshots/exercise-1/e1-15-minimum-password-length-nav.png)

16. Set the minimum length to **10 characters**.

    ![Set minimum password length](screenshots/exercise-1/e1-16-minimum-password-length.png)

17. The Explain tab covers how length strengthens a password against brute-force attacks.

    ![Minimum password length – explanation](screenshots/exercise-1/e1-17-minimum-password-length-explain.png)

18. Open **Password must meet complexity requirements**.

    ![Complexity navigation](screenshots/exercise-1/e1-18-complexity-nav.png)

19. **Enable** complexity requirements — passwords must mix character types and avoid the user's name.

    ![Enable complexity](screenshots/exercise-1/e1-19-password-complexity-enabled.png)

20. The Explain tab lists the exact complexity rules enforced.

    ![Complexity – explanation](screenshots/exercise-1/e1-20-password-complexity-explain.png)
>

---

## Task 3 – Configure the Account Lockout Policy

21. Navigate to **Account Lockout Policy**.

    ![Account lockout policy](screenshots/exercise-1/e1-21-account-lockout-policy-nav.png)

22. The lockout settings are listed.

    ![Account lockout settings](screenshots/exercise-1/e1-22-account-lockout-settings.png)

23. **Account lockout duration** — set to **30 minutes**.

    ![Account lockout duration](screenshots/exercise-1/e1-23-account-lockout-duration.png)

24. The Explain tab describes how long a locked account stays locked.

    ![Lockout duration – explanation](screenshots/exercise-1/e1-24-account-lockout-duration-explain.png)

25. **Account lockout threshold** — the Explain tab covers how many failed attempts trigger a lockout.

    ![Lockout threshold – explanation](screenshots/exercise-1/e1-25-account-lockout-threshold-explain.png)

26. Back in the lockout policy list.

    ![Lockout policy list](screenshots/exercise-1/e1-26-account-lockout-list.png)

27. **Reset account lockout counter after** — the Explain tab describes the window before the failed-attempt counter resets.

    ![Reset lockout counter – explanation](screenshots/exercise-1/e1-27-reset-lockout-counter-explain.png)

28. The account policies are configured.

    ![Account policies configured](screenshots/exercise-1/e1-28-account-policies-configured.png)
>

---

## Task 4 – Scope and Apply the Policy

29. Select the **Password Policy** GPO and open its **Scope** tab to adjust **Security Filtering**.

    ![GPO security filtering](screenshots/exercise-1/e1-29-gpo-security-filtering.png)

30. Add a group — click **Advanced** in the object picker.

    ![Security filtering – advanced](screenshots/exercise-1/e1-30-security-filtering-advanced.png)

31. Click **Find Now** to list available objects.

    ![Advanced – find now](screenshots/exercise-1/e1-31-advanced-find-now.png)

32. Select **Domain Users**.

    ![Select Domain Users](screenshots/exercise-1/e1-32-select-domain-users.png)

33. Confirm the selection.

    ![Domain Users confirmed](screenshots/exercise-1/e1-33-domain-users-confirmed.png)

34. **Domain Users** now appears in Security Filtering — the policy applies to all domain user accounts.

    ![Security filtering set](screenshots/exercise-1/e1-34-security-filtering-set.png)

35. Review the GPO scope.

    ![GPO scope](screenshots/exercise-1/e1-35-gpo-scope.png)

36. Open **PowerShell** to force the policy to apply immediately.

    ![Open PowerShell](screenshots/exercise-1/e1-36-open-powershell.png)

37. Run `gpupdate /force` to pull the new policy right away rather than waiting for the normal refresh cycle.

    ```powershell
    gpupdate /force
    ```

    ![gpupdate /force](screenshots/exercise-1/e1-37-gpupdate-force.png)

38. Both computer and user policy updates complete successfully.

    ![gpupdate complete](screenshots/exercise-1/e1-38-gpupdate-complete.png)

---

[← Back to Lab Overview](../README.md) | [Next: Exercise 2 – User Accounts & Groups →](../exercise-2-user-accounts-and-groups/README.md)
