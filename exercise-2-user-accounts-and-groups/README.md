# Exercise 2 – User Accounts & Groups

[← Back to Lab Overview](../README.md)

---

## Overview

**Active Directory (AD)** provides centralized management of user accounts, computer accounts, and security groups across an enterprise network. Through **Role-Based Access Control (RBAC)**, administrators can assign permissions based on job responsibilities while reducing unnecessary access to sensitive resources.

In this exercise, I explored **Active Directory Users and Computers (ADUC)** to manage user identities, group memberships, and access permissions within a Windows domain.

**Key Configuration Activities:**

- **User Management:** Create and configure Active Directory user accounts.
- **Computer Management:** Manage domain-joined computer accounts.
- **Security Groups:** Organize users into groups for centralized permission management.
- **Access Control:** Apply role-based permissions to support the principle of least privilege.

> **This exercise demonstrates practical experience in Windows Server administration, Active Directory management, and enterprise identity and access control.**
## Device

- **corp-dc-001** – Windows Server – Domain Controller / Active Directory Users and Computers (192.168.20.2)

---

## Task 1 – Create a User Account

1. Open **Server Manager → Tools → Active Directory Users and Computers**.

   ![Open Active Directory Users and Computers](screenshots/exercise-2/e2-01-open-active-directory-users-and-computers.png)

2. Right-click the **Users** container and choose **New → User**.

   ![New user](screenshots/exercise-2/e2-02-new-user.png)

3. Enter the account details — first name **Ron**, last name **Simmons**, logon name **Ron.Simmons**.

   ![New user details](screenshots/exercise-2/e2-03-new-user-details.png)

4. Set a password and tick **User must change password at next logon** so the account owner sets their own secret on first use.

   ![Set user password](screenshots/exercise-2/e2-04-set-user-password.png)

5. Review the summary and finish — the account is created.

   ![Confirm new user](screenshots/exercise-2/e2-05-confirm-new-user.png)

6. Open the new user's **Properties**.

   ![Open user properties](screenshots/exercise-2/e2-06-open-user-properties.png)

7. Review the **Account** tab — logon names and account settings.

   ![Account tab](screenshots/exercise-2/e2-07-account-tab.png)

8. Review the **Account options** and expiration settings.

   ![Account options](screenshots/exercise-2/e2-08-account-options.png)

> 🔎 **"User must change password at next logon" matters.** It means the administrator never knows the account's working password — the user sets it themselves on first logon. That removes a shared-secret weak point and keeps accountability clean: only the account owner knows the credential.

---

## Task 2 – Add the User to Groups

9. Right-click the user and choose **Add to a group**.

   ![Add to a group](screenshots/exercise-2/e2-09-add-to-a-group.png)

10. In the group picker, click **Advanced**.

    ![Select groups – advanced](screenshots/exercise-2/e2-10-select-groups-advanced.png)

11. Click **Find Now** to list the groups.

    ![Advanced – find now](screenshots/exercise-2/e2-11-advanced-find-now.png)

12. Select the **Administrators** group.

    ![Select Administrators](screenshots/exercise-2/e2-12-select-administrators.png)

13. Confirm the selection.

    ![Administrators confirmed](screenshots/exercise-2/e2-13-administrators-confirmed.png)

14. The add-to-group operation completes successfully.

    ![Add to group success](screenshots/exercise-2/e2-14-add-to-group-success.png)

15. Open the user's **Properties → Member Of** tab to review group membership.

    ![Member Of](screenshots/exercise-2/e2-15-open-properties-member-of.png)

16. **Administrators** now appears in the membership list.

    ![Member of Administrators](screenshots/exercise-2/e2-16-member-of-administrators.png)

17. The full membership list — Administrators and Domain Users.

    ![Member of list](screenshots/exercise-2/e2-17-member-of-list.png)

18. Reviewing the **Administrators** group's own properties (scope and type).

    ![Administrators group properties](screenshots/exercise-2/e2-18-administrators-group-properties.png)

19. To add another group, click **Add** on the Member Of tab.

    ![Member Of – add](screenshots/exercise-2/e2-19-member-of-add.png)

20. Click **Advanced** in the picker.

    ![Select groups – advanced](screenshots/exercise-2/e2-20-select-groups-advanced-2.png)

21. Click **Find Now**.

    ![Advanced – find now](screenshots/exercise-2/e2-21-advanced-find-now-2.png)

22. Select **Remote Management Users**.

    ![Select Remote Management Users](screenshots/exercise-2/e2-22-select-remote-management-users.png)

23. Confirm the selection.

    ![Remote Management Users confirmed](screenshots/exercise-2/e2-23-remote-management-users-confirmed.png)

24. The membership list now includes **Administrators**, **Domain Users** and **Remote Management Users** — access granted entirely through group membership.

    ![Member of updated](screenshots/exercise-2/e2-24-member-of-updated.png)

> 🔎 **A note on least privilege.** Adding an account to **Administrators** grants broad, powerful rights — appropriate here to demonstrate group-based access, but in production that membership is handed out sparingly and reviewed regularly. The principle is to grant the *least* access a role needs, and groups make it just as easy to keep access tight as to grant it broadly.

---

> ### 🎤 Stakeholder Takeaway
>
 Implemented centralized **user and group management** through Active Directory to simplify access control across the Windows domain.
>
 - **Role-Based Access:** Assigned permissions through security groups based on job responsibilities.
 - **Centralized Management:** Simplified granting, modifying, and revoking user access.
 - **Security:** Supported least-privilege access and reduced the risk of unnecessary permissions.
>
> **Business Impact:** Improves administrative efficiency, strengthens access security, and simplifies user access audits.
---

[← Previous: Exercise 1 – Password & Account Lockout Policies](../exercise-1-password-and-account-lockout-policies/README.md) | [Back to Lab Overview](../README.md) | [Next: Exercise 3 – Permissions & Access Controls →](../exercise-3-permissions-and-access-controls/README.md)
