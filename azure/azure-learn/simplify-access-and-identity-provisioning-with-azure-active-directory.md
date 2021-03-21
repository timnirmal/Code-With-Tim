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

## Define the right access to safeguard identities and data

100 XP

* 5 minutes

Azure Active Directory \(AD\) lets you collaborate internally as well as externally. Users can join groups, invite guests, connect to cloud apps, and work remotely from their work or personal devices. The convenience of self-service however, has led to a need for better access management capabilities.

How do you:

* Ensure new employees have the right access to be productive?
* Ensure access is removed when people—especially guests—leave or change teams?
* Ensure access rights aren't excessive, which can indicate a lack of control over access and lead to audit findings?
* Engage with resource owners to ensure they regularly review who has access to their resources?

![Azure access reviews](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/azure-access-reviews.png)

To help you address these questions, Azure AD has developed a capability called **access reviews**.

Azure AD access reviews help you recertify and audit users' access to resources, ensuring that their access is appropriate and reviewed on a regular basis. Access reviews enable organizations to efficiently address excess access risks and provide more visibility about them to users in departments beyond IT. If you're only concerned about guests, then access reviews make it easy to scope the review for guests only.

To understand how Azure AD access reviews help you manage access, consider four sets of users:

* **Members of Office groups**. Office 365 users can create as many groups as they wish. Access reviews allow you to manage membership of those groups.
* **Members of security groups**. Access reviews help you manage users both cloud-only or synchronized from on-prem to cloud who should or shouldn't be in a group.
* **Users who have been directly assigned to an application**.
* **Guest users**. If you're only concerned about guests who have been invited to your directory, we make it easy to scope the review to be on guests only.

### Flexibility in reviewer assignments <a id="flexibility-in-reviewer-assignments"></a>

Azure AD access review provides flexibility in how you assign the reviewers. You can assign the owners of a group directly so they can review the access of a group. Or you can select multiple specific individuals as reviewers.

### When to use access reviews <a id="when-to-use-access-reviews"></a>

Azure AD Access Reviews can be used in a variety of circumstances:

* **Too many users in privileged roles**. It's a good idea to check how many users have administrative access, how many of them are Global Administrators, and if there are any invited guests or partners that have not been removed when their tasks are complete.
* **When automation is not feasible**. You can create rules for dynamic membership in security groups or Office 365 Groups. But sometimes HR data is not in Azure AD, or users still need access after leaving the group. You can then create a review of that group to ensure those who still need it have continued access.
* **When a group is repurposed**. If you have a group that is going to be synced to Azure AD, it would be useful to ask the group owner to review the group membership prior to the group being used in a different risk context.
* **For business critical data access**. For certain resources, you might require people outside of IT to regularly sign out and justify why they need continued access.
* **To maintain a policy's exception list**. As the IT administrator, you can manage policy exceptions, avoid policy error exceptions, and provide auditors with proof that these exceptions are reviewed regularly.
* **To confirm group owners still need guests in their groups**. Employee access might be automated with some on-premises access management, but that’s not the case for guests. If a group gives guests access to business sensitive content, then it's the group owner's responsibility to confirm the guests still have a legitimate business need for access.

You can set up recurring access reviews of users at set frequencies such as weekly, monthly, quarterly, or annually, and the reviewers will be notified at the start of each review. A user-friendly interface and smart recommendations make approving or denying access easy.



## Establish an identity governance process

100 XP

* 8 minutes

With Azure Active Directory \(Azure AD\), you can easily ensure that users have appropriate access. You can ask the users themselves or a decision maker to participate in an access review and recertify \(or attest\) to users' access. The reviewers can give their input on each user's need for continued access based on suggestions from Azure AD. When an access review is finished, you can then make changes and remove access from users who no longer need it.

### Begin an access review <a id="begin-an-access-review"></a>

To begin an access review, select the Azure AD group or application you want to manage access to. Decide whether you want individual users to review their own access, or one or more users review access for everyone. Then:

1. Navigate to the **Identity Governance** page.

   ![Step 1 The Identity Governance page](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/01-identity-governance-page.png)

2. If this is your first time using access reviews, select **Onboard** and **Onboard Now**.

   ![Step 2 Select Onboard and Onboard Now](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/02-onboard.png)

3. Select **Create an access review** from the Getting started page

   ![Step 3 Create an access review](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/03-create-access-review.png)

4. On the Access Review screen, provide a **name**, **Start date**, **frequency/duration**, and **end date**. These settings will apply to either members of a group or users assigned to an application. Select the group or application along with the reviewers:

   ![Step 4 Enter needed data](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/04-enter-needed-data.png)

5. Once the review is created, the access review will initialize and then start on the assigned date.

   ![Step 5 Initialize and start](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/05-initialize-start.png)

6. Reviewers assigned to the access review will receive an email from Microsoft, prompting them to review access:

   ![Step 6 Email to review access](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/06-email-review-access.png)

7. On the Access review page, they can select either the groups and apps that require access reviews, or the access packages:

   ![Step 7 Review access packages](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/07-access-reviews-webpage.png)

8. Once the reviewer has opened the access review, they are able to approve or deny the access. Here three users are selected and denied for access to the Intune Administrators group:

   ![Step 8 Approve or deny access](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/08-intune-admin-confirm-deny.png)

9. The Identity Governance access review pane then updates with the results of the access review, and users denied access are removed from the group.

   ![Step 9 Access review pane update](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-provisioning/media/09-access-review-pane.png)



## Summary

100 XP

* 1 minute

In this module, you learned about identity governance and how you can safeguard access to your organization’s data.

Now that you have completed this module, you should be able to:

* Define single sign-on.
* Understand identity governance.
* Explain how to perform an access review.

