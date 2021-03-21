# Define identity and access management in Azure Active Directory



## Introduction to identity technology

100 XP

* 3 minutes

**Azure Active Directory \(Azure AD\)** is Microsoft’s next evolution of identity and access management solutions for the cloud. Microsoft introduced Active Directory Domain Services in Windows 2000 to give organizations the ability to manage multiple on-premises infrastructure components and systems using a single identity per user. Azure AD takes this approach to the next level by providing organizations with an Identity as a Service \(IDaaS\). Azure Active Directory \(Azure AD\) helps your employees sign in and access:

* External resources, such as Microsoft Office 365, the Azure portal, and thousands of other SaaS applications.
* Internal resources, such as apps on your corporate network and intranet, along with any cloud apps developed by your own organization.

![Manage all your apps from one central location](https://docs.microsoft.com/en-us/learn/m365/m365-identity-overview/media/manage-apps-central-location.png)

Most IT administrators are familiar with Active Directory Domain Services concepts. The following table outlines the differences and similarities between Active Directory concepts and Azure Active Directory.

| TABLE 1 |  |  |
| :--- | :--- | :--- |
| Concept | Active Directory | Azure Active Directory |
| **Users** |  |  |
| Admin management | Organizations will use a combination of domains, organizational units, and groups in AD to delegate administrative rights to manage the directory and resources it controls. | Azure AD provides built-in roles with its role-based access control \(RBAC\) system, with limited support for creating custom roles to delegate privileged access to the identity system, the apps, and resources it controls. Managing roles can be enhanced with Privileged Identity Management \(PIM\) to provide just-in-time, time-restricted, or workflow-based access to privileged roles. |
|  |  |  |
| Credential management | Credentials in Active Directory is based on passwords, certificate authentication, and smartcard authentication. Passwords are managed using password policies that are based on password length, expiry, and complexity. | Azure AD uses intelligent password protection for cloud and on-premises. Protection includes smart lockout plus blocking common and custom password phrases and substitutions. Azure AD significantly boosts security through multi-factor authentication and passwordless technologies, like FIDO2. Azure AD reduces support costs by providing users with a self-service password reset system. |
| **Apps** |  |  |
| Infrastructure apps | Active Directory forms the basis for many infrastructure on-premises components, for example, DNS, DHCP, IPSec, WiFi, NPS, and VPN access. | In a new cloud world, Azure AD is the new control plane for accessing apps versus relying on networking controls. When users authenticate, conditional access \(CA\) will control which users will have access to which apps under required conditions. |
| SaaS apps | Active Directory doesn't support SaaS apps natively and requires federation systems, such as AD FS. | SaaS apps supporting OAuth2, SAML, and WS-\* authentication can be integrated to use Azure AD for authentication. |
| **Devices** |  |  |
| Mobile | Active Directory doesn't natively support mobile devices without third-party solutions. | Microsoft’s mobile device management solution, Microsoft Intune, is integrated with Azure AD. Microsoft Intune provides device state information to the identity system to evaluate during authentication. |
| Windows desktops | Active Directory provides the ability to domain join Windows devices to manage them using Group Policy, System Center Configuration Manager, or other third-party solutions. | Windows devices can be joined to Azure AD. Conditional access can check if a device is Azure AD joined as part of the authentication process. Windows devices can also be managed with Microsoft Intune. In this case, conditional access, will consider whether a device is complaint \(for example, up-to-date security patches and virus signatures\) before allowing access to the apps. |

With Microsoft's access and information protection solutions, you can deploy and configure access to corporate resources across your on-premises environment and cloud applications. And you can do it while protecting corporate information. The following are scenarios provided by the latest identity and access technologies:

* Secure access to company resources from any location on any device
* Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications
* Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications
* Manage Risk with Conditional Access Control
* Configure Certificate Enrollment Web Service for certificate key-based renewal on a custom port

## Understand the importance of identity

100 XP

* 3 minutes

Today, analyst firms report that the average enterprise’s employees collectively use more than 300 software-as-a-service applications \(and some estimates are much higher\). That number is rapidly expanding. Between the hyper-growth of these apps, the rate at which they change and the business demand to harness new cloud capabilities for business transformation, it’s challenging to keep up. Relying on an on-premises identity solution as the control point makes connecting to all these cloud applications a nearly impossible task. If you include all the user devices, guest accounts, and connected objects, you have a management and security nightmare.

![300 percent increase in identity attacks](https://docs.microsoft.com/en-us/learn/m365/m365-identity-overview/media/increase-identity-attacks.png)

With cloud-based identity as the control point, you can help users be more productive by providing access to apps and devices that are on-premises or in the cloud from virtually anywhere and do so with incredible agility. Whether you’re just getting started on your cloud journey or want to accelerate your identity modernization, Azure AD can help you connect all your applications to achieve your business productivity and security goals.

![Consistent single-sign-on to legacy apps](https://docs.microsoft.com/en-us/learn/m365/m365-identity-overview/media/consistent-sso-legacy-apps.png)

## Understand how identity is core to security

100 XP

* 3 minutes

![Identity is the new security perimeter](https://docs.microsoft.com/en-us/learn/m365/m365-identity-overview/media/identity-new-security-perimeter.png)

Whether your assets are hosted on-premises or in the cloud, the security **perimeter** that separates users and data from outside threats can no longer be drawn using network lines. The perimeter is now drawn by identity components of authentication and authorization that span across all your devices, services, hosts, and networks.

While the network perimeter keeps a basic security role, it can no longer guide the security defense strategy because:

* Adversaries have demonstrated a consistent and ongoing ability to penetrate network perimeters using phishing attacks.
* Organizational data, devices, and users often exist and operate outside traditional network boundaries \(whether sanctioned by IT or not\).
* Port and protocol definitions and exceptions have failed to keep up with the complexity of services, applications, devices, and data.

Organizations need to adopt different security philosophies and mindsets that are based on rigorous management of authentication and authorization, not firewall rules and exceptions.

Administrators are in control and need protection. The most important identities to protect are the administrators of on-premises and cloud systems, especially identity systems like Active Directory and Azure Active Directory. These administrators have access to all the data hosted on their systems and should be protected, monitored, and restricted appropriate with their high level of responsibility.



## Summary

100 XP

* 1 minute

In this module, you learned about identity and access management in Microsoft 365 and why identity is a core component of your organization’s security posture.

Now that you have completed this module, you should be able to:

* Define the latest identity technologies.
* Understand the value of securing your identity.
* Explain how identity is core to security.



