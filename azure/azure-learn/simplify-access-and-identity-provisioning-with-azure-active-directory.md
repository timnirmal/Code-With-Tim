# Simplify access and identity provisioning with Azure Active Directory



## Introduction to identity provisioning

100 XP

* 3 minutes

### Sign on seamlessly to all connected apps <a id="sign-on-seamlessly-to-all-connected-apps"></a>

Single sign-on \(SSO\) adds security and convenience to signing on to applications in Azure Active Directory \(Azure AD\).

**With single sign-on**, users sign on once to access domain-joined devices, company resources, software as a service \(SaaS\) applications, and web applications. After signing on, the user can launch applications from the Office 365 portal or the Azure AD MyApps access panel. Administrators can centralize user account management and automatically add or remove user access to applications based on group membership.

**Without single sign-on**, by contrast, users must remember application-specific passwords and log into each application individually. IT staff needs to create and update user accounts for each application such as Office 365, Box, and Salesforce.

![Enable a seamless user experience with single sign-on](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/enable-sso.png)

### Configure single sign-on <a id="configure-single-sign-on"></a>

There are several ways to configure an application for single sign-on, depending on how the application is configured for authentication.

* Cloud applications use OpenID Connect, OAuth, SAML, password-based, linked, or disabled methods for single sign-on.
* On-premises applications use password-based, Integrated Windows Authentication, header-based, linked, or disabled methods for single sign-on. The on-premises choices work when applications are configured for Application Proxy. Azure AD Application Proxy is a feature of Azure AD that supports SSO and enables users to access on-premises web applications from a remote client, removing the need for a VPN or a reverse proxy.

## Be proactive with identity governance

100 XP

* 24 minutes

![identity governance](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/identity-governance.png)

Azure Active Directory \(Azure AD\) Identity Governance allows you to balance your organization's need for both security and employee productivity. Azure AD ensures the right people have the right access to the right resources. Azure AD and Enterprise Mobility + Security features allow you to mitigate access risk by protecting, monitoring, and auditing access to critical assets -- while ensuring employee and business partner productivity.

Access is easy to grant but much harder to keep track of. Not only do you need to track who is given access to what resources, you also need to be able to revoke access in a timely manner when it is no longer needed. Plus, access controls should apply to both internal and external users.

Azure AD Identity Governance helps manage access using the following capabilities:

* Ensuring that only authorized users have access based on policies.
* Providing employees and guest users with workflows to request access.
* Establishing regular access reviews to validate if access if still needed.
* Establishing effective controls with time-limited access for privileged roles assignments.

#### Explore how to enable business-to-business collaboration in Azure AD <a id="explore-how-to-enable-business-to-business-collaboration-in-azure-ad"></a>

View a [video version](https://www.microsoft.com/videoplayer/embed/RE4ChU3) of the interactive guide \(captions available in more languages\).

[![Enable B2B Collaboration with Azure AD](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/interactive-enable-b2b-collaboration.png)](https://mslearn.cloudguides.com/guides/Enable%20B2B%20Collaboration%20in%20Azure%20AD)

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.

Identity Governance helps organizations achieve a balance between productivity and security. Just as important as how quickly can a new person access the resources they need, is how should that person’s access change when they leave. Identity lifecycle management is the foundation of Identity Governance. And effective governance at scale requires modernizing the identity lifecycle management infrastructure for applications.

![User access lifecycle](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/user-access-lifecycle.png)



