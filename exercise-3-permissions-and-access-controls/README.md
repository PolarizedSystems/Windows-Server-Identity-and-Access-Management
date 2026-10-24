# Exercise 3 – Permissions & Access Controls

[← Back to Lab Overview](../README.md)

---

## Overview

**Permissions and access controls** are essential for securing enterprise infrastructure and ensuring users have appropriate access to network resources. Through **Active Directory delegation**, administrators can assign specific administrative responsibilities without granting full system privileges.

In this exercise, I explored **delegation of control in Active Directory** to distribute administrative tasks while maintaining centralized security oversight.

**Key Configuration Activities:**

- **Permission Management:** Define and manage administrative access rights.
- **Delegation of Control:** Assign specific responsibilities to designated users or groups.
- **Administrative Tasks:** Delegate functions such as user account creation and password resets.
- **Least Privilege:** Limit administrative permissions based on assigned responsibilities.

> **This exercise demonstrates practical experience in Active Directory administration, delegated access management, and enterprise security controls.**
## Device

- **corp-dc-001** – Windows Server – Domain Controller / Active Directory Users and Computers (192.168.20.2)

---

## Task 1 – Delegate Control

1. In Active Directory Users and Computers, right-click the **Users** container and choose **Delegate Control**.

   ![Delegate control](screenshots/exercise-3/e3-01-delegate-control.png)

2. The **Delegation of Control Wizard** opens.

   ![Delegation wizard welcome](screenshots/exercise-3/e3-02-delegation-wizard-welcome.png)

3. On the users-or-groups screen, click **Add** to choose who receives the delegated rights.

   ![Add users or groups](screenshots/exercise-3/e3-03-add-users-or-groups.png)

4. Select **Ron Simmons** as the delegate.

   ![Select Ron Simmons](screenshots/exercise-3/e3-04-select-ron-simmons.png)

5. Choose the tasks to delegate — **Create, delete, and manage user accounts** and **Reset user passwords and force password change at next logon** — a tightly scoped grant, not blanket administrative power.

   ![Tasks to delegate](screenshots/exercise-3/e3-05-tasks-to-delegate.png)

6. Finish the wizard — the delegated rights are now in effect.

   ![Delegation complete](screenshots/exercise-3/e3-06-delegation-complete.png)

> 🔎 **What this account can and can't do now.** Ron Simmons can create, manage, and reset passwords for user accounts in this container — the day-to-day work of a help-desk or junior admin. What he *can't* do is modify group policy, touch domain controllers, or alter the domain's structure, because none of those rights were delegated. That gap is the whole point: capability matched precisely to need.

---

> ### 🎤 Stakeholder Takeaway
>
> "Staff get exactly the administrative authority their job calls for — and not a scrap more. A technician can reset passwords and manage user accounts without ever being handed domain-wide control, so a mistake or a compromised help-desk login can't cascade into a full takeover. It's how we let people do their jobs efficiently while keeping the most powerful rights locked down to the few who genuinely need them."

---

[← Previous: Exercise 2 – User Accounts & Groups](../exercise-2-user-accounts-and-groups/README.md) | [Back to Lab Overview](../README.md) | [Next: Exercise 4 – Auditing →](../exercise-4-auditing/README.md)
