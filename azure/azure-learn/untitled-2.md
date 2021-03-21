# Secure administrator accounts in Azure Active Directory

## Introduction to securing administrator accounts

100 XP

* 3 minutes

### Secure devices <a id="secure-devices"></a>

For sensitive tasks, Privileged Access Workstations \(PAWs\) provide a dedicated operating system that is protected from Internet attacks and threat vectors. Separating these sensitive tasks and accounts from daily use workstations and devices provides very strong protection from phishing attacks, application and OS vulnerabilities, various impersonation attacks, and credential theft attacks such as keystroke logging, Pass-the-Hash, and Pass-The-Ticket.

![Privileged Access Workstations \(PAWs\)](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/paw.png)

In simplest terms, PAWs are hardened and locked down workstations designed to provide high security assurances for sensitive accounts and tasks. PAWs are recommended for administration of identity systems, cloud services, and private cloud fabric as well as sensitive business functions.

In order to provide the greatest security, PAWs should always run the most up-to-date and secure operating system available. Microsoft strongly recommends Windows 10 Enterprise, which includes several additional security features \(in particular, Credential Guard and Device Guard\) not available in other editions.

PAW security controls are focused on mitigating high impact and high probability risks of compromise. These include mitigating attacks on the environment and risks that can decrease the effectiveness of PAW controls over time:

* **Internet attacks**. Most attacks originate directly or indirectly from internet sources and use the internet for exfiltration and command and control \(C2\). Isolating the PAW from the open internet is critical to ensuring it’s not compromised.
* **Usability risk**. If a PAW is too difficult to use for daily tasks, administrators will find workarounds to make their jobs easier. Frequently, these workarounds open the workstation and accounts to significant security risks, so it's critical to involve and empower PAWs users to mitigate these usability issues securely.
* **Environment risks**. Because other computers and accounts in the environment are exposed to risks directly or indirectly, a PAW must be protected against attacks from those compromised assets in the production environment. This requires minimizing the use of management tools and accounts that have access to the PAWs.
* **Supply chain tampering**. While it's impossible to remove all possible risks of tampering in the supply chain for hardware and software, taking a few key actions can mitigate readily available attack vectors, including validating the integrity of all installation media and using a trusted and reputable supplier for hardware and software.
* **Physical attacks**. Because PAWs can be physically mobile and used outside of physically secure facilities, they must be protected against attacks that leverage unauthorized physical access to the computer.

Microsoft uses the PAW architectural approach on both its own systems as well as on those of its customers. Microsoft uses administrative workstations internally in several capacities including administration of Microsoft IT infrastructure, Microsoft cloud fabric infrastructure development and operations, and other high value assets.

## Understand isolated identity

100 XP

* 5 minutes

Securing privileged access is a critical first step to securing business assets in a modern organization. The security of business assets in an IT organization depends on the integrity of the privileged accounts used for administration, management, and development. Privileged accounts like administrators of Active Directory Domain Services have direct or indirect access to most or all assets in an IT organization, making a compromise of these accounts a significant business risk. Cyber-attackers often target these accounts and other elements of privileged access using credential theft attacks like Pass-the-Hash and Pass-the-Ticket. An attacker that gains control of an administrative account can use those privileges to increase their impact in the target organization as depicted below:

![An attacker that gains control of an administrative account can use those privileges to increase their impact in the target organization.](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/attackers.png)

Protecting privileged access against determined adversaries requires you to take a complete and thoughtful approach to isolate these systems from risks.

To help separate internet risks \(phishing attacks, web browsing\) from privileged access account risks, create a dedicated account for all personnel with privileged access. Administrators should not be browsing the web, checking their email, or doing day to day productivity tasks with highly privileged accounts.

![Active directory tier model](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/active-directory-tier-model.png)

Implementing a tiered model can prevent an escalation of privilege path for an attacker who is using stolen credentials. The tier model is defined by the following rules:

* Each administrative resource \(group, account, servers, workstation, Active Directory object, or application\) are classified as only one tier.
* Personnel with responsibilities at multiple tiers have separate administrative accounts created for each required tier. Any account that currently logs on to multiple tiers are split into multiple accounts, each of which fits within only one tier definition. These accounts are also required to have different passwords.
* Administrative accounts may not control higher-tier resources through administrative access such as access control lists \(ACLs\), application agents, or control of service accounts. Accounts that control a higher tier may not log on to lower-tier computers because logging on to such a computer might expose and inadvertently grant control of the account credentials and privileges assigned to that account. Under some specific exceptions, a feature that supports Remote Desktop Protocol \(RDP\) with restricted admin mode could be used without exposing credentials.
* Administrative accounts may control lower-tier resources as required by their role, but only through management interfaces that are at the higher tier and that do not expose credentials—for example, domain admin accounts \(tier 0\) managing server admin Active Directory account objects \(tier 1\) through Active Directory management consoles on a domain controller \(tier 0\).

To further prevent the risk of escalated credentials, consider the following recommended practices:

* Do not use the same password for domain and local accounts.
* Limit valid lifetime of credentials. In other words, balance usability \(time between entering credentials\) and security \(credential exposure duration\).
* Protocol considerations including:
  * Kerberos natively expires reusable credentials \(ticket granting ticket lifetime and renewal lifetime\).
  * NTLM credential \(NT hash\) is valid until password changes.
* Various options grant and expire privileges, each with caveats:
  * Group membership
  * Dynamic account creation
  * Scripted actions

Although the previous information focuses on Active Directory environments, much of the same guidance applies to securing Azure Active Directory admin accounts. For example, Microsoft recommends creating dedicated Microsoft 365 global administrator accounts that are used only when necessary, and that those accounts be secured via multi-factor authentication. Additionally, for privileged access, Azure Active Directory admin accounts can leverage just-in-time privileges through Azure AD Privileged Identity Management to ensure administrative credentials are only being used when required.

For Azure Active Directory, also consider creating emergency access--or “break glass”--accounts. Emergency access accounts help restrict privileged access within an Azure AD organization. These accounts are highly privileged and aren't assigned to specific individuals. Emergency access accounts are limited to "break glass" scenarios where normal administrative accounts can't be used \(such as if a federated on-premises identity provider isn’t available\). If you don't see any global admin cloud-only accounts using the \*.onmicrosoft.com domain \(for "break glass" emergency access\), create at least two of these accounts.  

## Learn about just-in-time privileges

100 XP

* 7 minutes

Just in time \(JIT\) access is a model in which users receive temporary permissions to perform privileged tasks which prevents malicious or unauthorized users from gaining access after the permissions have expired. Access is granted only when users need it.

![Azure AD Privileged Identity Management \(PIM\)](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/pim.png)

Azure AD Privileged Identity Management helps you manage privileged administrative roles across Azure AD, Azure resources, and other Microsoft Online Services. \(For Active Directory Domain Services, use Microsoft Identity Manager's Privileged Access Manager capability\). In a world where privileged identities are assigned and forgotten, Privileged Identity Management provides solutions like just-in-time access, request approval workflows, and fully integrated access reviews so you can identify, uncover, and prevent malicious activities of privileged roles in real time. Deploying Privileged Identity Management to manage your privileged roles throughout your organization greatly reduces risk while surfacing valuable insights about the activities of your privileged roles.

![Manage your privileged access screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/quick-start.png)

### Manage risk <a id="manage-risk"></a>

You can secure your organization by enforcing the principles of least privilege and just-in-time access. By minimizing the number of permanent assignments of users to privileged roles and enforcing approvals and MFA for elevation, you greatly reduce security risks related to privileged access. Enforcing least privilege and just-in-time access will also allow you to view a history of access to privileged roles so you can track down security issues as they happen.

### Address compliance and governance <a id="address-compliance-and-governance"></a>

Deploying Privileged Identity Management creates an environment for on-going identity governance. Just-in-time elevation of privileged identities provides a way for Privileged Identity Management to keep track of privileged access activities in your organization. You can also view and receive notifications for all assignments of permanent and eligible roles. Through access review, you can regularly audit and remove unnecessary privileged identities and make sure your organization complies with the most rigorous identity, access, and security standards.

### Steps to enable Privileged Identity Management <a id="steps-to-enable-privileged-identity-management"></a>

First, you need to set up Privileged Identity Management so that users are eligible for privileged roles. In the Azure portal:

1. Open the **Azure AD Privileged Identity Management** blade.
2. Select **Azure AD roles** and then **Role settings**:

   ![Role settings screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/settings.png)

3. Select the role you would like to require just in time privileges. Here, we selected the Intune Administrator role:

   ![Intune administrator role selected in Role settings details screen ](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/role-setting-details.png)

4. Click **Edit** to identify the tasks required to receive privileges. Here, we set the maximum activation duration to 8 hours, required Azure MFA for activation, and required justification. We also required an approver to activate.

   ![Activation screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/activate.png)

   When assigning a privileged identity-managed role, you can choose from those two assignment types – **eligible** and **active**. Eligible assignments require the member of the role to perform an action to use the role. Actions might include performing a multi-factor authentication \(MFA\) check, providing a business justification, or requesting approval from designated approvers. Active assignments don't require the member to perform any action to use the role. Members assigned as active have privileges assigned at all times. In the **roles** settings, we can configure the expiration duration for both of these assignment types.

   ![Assignment screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/assignment.png)

5. Provide notification rules, such that the appropriate members of your organization are aware of the permissions users have.

   ![Notification screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/notification.png)

6. Now that you’ve configured and updated the settings for a role, in the Privileged Identity Management pane, add a member to the role by selecting **Roles -&gt; + Add Assignments**. Then, select the role to be configured and members to assign.

   ![Add assignments screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/add-assignments.png)

7. Then provide the assignment type:

   ![Assignment type screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/setting.png)

8. Click **assign**.

Now when the assigned users log in to the Privileged Identity Management blade of the Azure portal, they will be able to Activate the roles they were assigned:

![Role activation screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/my-roles.png)

Because of the settings we configured, to activate the Intune administrator role users need to provide a justification:

![Intune administrator role users need to provide a justification](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/activate.png)

The approver will then receive a notification and can approve the request by selecting Approve Requests in the Privileged identity Management portal:

![Request approval screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/approve-requests.png)

After reviewing the justification that the user provided, the approver can approve the request and also provide their own justification:

![Approver justification screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/admin.png)

Then the user sees the role as Active within Privileged Identity Management and can access the assigned resources.

![Active roles screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-secure-administrators/media/azure-ad-roles.png)



## Summary

100 XP

* 1 minute

In this module, you learned about securing administrator accounts through secure devices, dedicated administrator accounts, and just-in-time privileges.

Now that you have completed this module, you should be able to:

* Define privileged access workstations.
* Describe how to create dedicated accounts for administrators improves security.
* Explain how Privileged Identity Management works.



