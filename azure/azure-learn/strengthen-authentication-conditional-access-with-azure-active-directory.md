# Strengthen authentication \(conditional access\) with Azure Active Directory

## Introduction to identity authentication

100 XP

* 3 minutes

### Modernize your authentication flows <a id="modernize-your-authentication-flows"></a>

To give your users easy access to your cloud apps, Azure Active Directory \(Azure AD\) supports a broad variety of authentication protocols including legacy authentication. Legacy authentication is a term that refers to an authentication request made by:

* Older Office clients that do not use modern authentication methods \(for example, Office 2010 client\).
* Any client that uses legacy mail protocols such as IMAP/SMTP/POP3.

Today the majority of all compromising sign-on attempts come from legacy authentication because it does not support multi-factor authentication \(MFA\). Even if you have an MFA policy enabled on your directory, a bad actor can authenticate using a legacy protocol and bypass MFA. The best way to protect your account from malicious authentication requests made by legacy protocols is to block these attempts altogether.

Modern authentication is a method of identity management that offers more secure user authentication and authorization. Specifically, modern authentication enables Microsoft Authentication Library \(MSAL\)-based sign-on for Office client apps across different platforms. This allows sign-on features such as multi-factor authentication \(MFA\), smart card, and certificate-based authentication to be enabled. If you have an MFA policy in place on your directory, modern authentication ensures that the user is prompted for MFA when required. It is the more secure alternative to legacy authentication protocols.  


## Enforce multi-factor authentication

100 XP

* 5 minutes

Multi-factor authentication \(MFA\) is a process where users are prompted during a sign-on event for additional forms of identification. This prompt could be to enter a code they receive on their cellphone or provide a fingerprint scan. Requiring a second form of authentication increases security since this additional authentication factor is far more difficult for an attacker to obtain or duplicate than a password.

Traditionally, Azure MFA would be enabled “per user.” In a per user environment, users enabled for MFA are prompted each time they sign into an application \(except on a trusted network\). This results in a poor user experience, because it doesn’t consider any other factors – such as device type, sign-on behavior, or client application.

A better way is to enable and use Azure MFA is with Conditional Access policies. Conditional Access lets you create and define policies that react to sign-on events and request additional actions before a user is granted access to an application or service. Azure MFA and Conditional Access policies give you the flexibility to enable MFA for users during specific sign-on events.

![Conditional access](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/conditional-access.png)

Conditional Access policies can be granular and specific, with the goal of empowering users to be productive wherever and whenever, but also protecting your organization. The following requirements are necessary to create a Conditional Access policy:

* A group of users need to be assigned to the policy.
* Once a group of users are assigned, you can define the cloud apps or actions that trigger the policy. These cloud apps or actions are the scenarios you decide that require additional processing, such as prompting for MFA. For example, you could decide that access to a financial application or use of management tools requires an additional verification prompt.
* You can also optionally specify a list of conditions, such as the device platform or location.
* After all the assignments are configured \(Azure AD group, cloud app or actions, and/or conditions\), you can select which controls are required to access the assignments. In the following example, we selected **Require multi-factor authentication**, which enforces MFA if a user meets our assignments.

![MFA required](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/multi-factor-authentication-required.png)

The **Require multi-factor authentication** control can be resolved by:

* Presence of the following claim in a token issued by the trusted federation service:
  * [https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod](https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod) = [https://schemas.microsoft.com/claims/multipleauthn](https://schemas.microsoft.com/claims/multipleauthn)
* Windows Hello for Business Primary Refresh Token \(PRT\) with strong authentication:
  * “ACR”: 2
* Azure MFA Service

One of the optional conditions you can configure for Conditional Access policies is **Locations**. For example, you can exclude a set of IP Ranges \(such as your corporate network\) from the MFA Required policy. Note that when you select the Locations condition in Conditional Access, there is an MFA Trusted IPs option:

[![Select locations for conditional access policy](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/select-locations.png)](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/select-locations-magnify.png#lightbox)

This refers to the Trusted IPs options that you can configure in the per-user MFA settings:

![Trusted IP options in MFA settings](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/service-settings.png)



## Reduce legacy authentication flows

100 XP

* 5 minutes

Before you can block legacy authentication in your directory, you need to first understand if your users have apps that use legacy authentication and how it affects your overall directory. Azure AD sign-in logs can be used to determine if you're using legacy authentication.

1. Navigate to the **Azure portal &gt; Azure Active Directory &gt; Sign-ins**.
2. Add the Client App column if it is not shown by clicking on **Columns &gt; Client App**.
3. Filter by **Client App** &gt; check all the **Legacy Authentication Clients** options presented.
4. Filter by **Status &gt; Success**.

   ![Azure AD Sign-in log](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/sign-in-log.png)

Filtering will only show you successful sign-on attempts that were made by the selected legacy authentication protocols. Clicking on each individual sign-on attempt will show you additional details. The Client App column or the Client App field under the Basic Info tab after selecting an individual row of data indicates which legacy authentication protocol was used. These logs indicate which users are still depending on legacy authentication and which applications are using legacy protocols to make authentication requests. For users that do not appear in these logs and are confirmed to be not using legacy authentication, implement a Conditional Access policy: block legacy authentication for these users only.

To create a Conditional Access policy to block legacy authentication, perform the following steps:

1. Create a new Conditional Access policy.
2. Target the users and groups who can be blocked.
3. Select **All Cloud apps**.
4. Under Conditions, select **Client apps \(preview\)**, set Configure to **Yes**, and check only the boxes **Mobile apps and desktop clients &gt; Other clients**.

   ![Create a new Conditional Access policy](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/new-conditional-access-policy.png)

5. Finally, under Access controls, select **Grant &gt; Block.**

   ![Select Grant &amp;gt; Block](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/access-controls-grant-block.png)

You should enable this policy as Report-only first, so you can learn which users are using legacy authentication.

Once you have a better idea who is using legacy authentication in your directory and which applications depend on it, the next step is upgrading your users to modern authentication. The following steps provide an overview of the path to modern authentication:

1. **Enable modern authentication**. Modern authentication is enabled by default for directories created on or after August 1, 2017. If your directory was created prior to this date, you'll need to manually enable modern authentication for your directory using PowerShell. For organizations actively using basic authentication for Exchange Online, be aware that basic authentication will be disabled for all tenants in the second half of 2021.

   The following PowerShell commands can be used to enable modern authentication:PowerShellCopy

   ```text
   - Exchange Online:
     Set-OrganizationConfig -OAuth2ClientProfileEnabled $True
   - Skype for Business Online:
     Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
   ```

2. **Update applications**. Once you have enabled modern authentication in your directory, you can start updating applications by enabling modern authentication for Office clients. Office 2016 or later clients support modern authentication by default. No extra steps are required.

   For Office 2013, the following registry keys are required:

   * HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL
     * Type REG\_DWORD
     * Value 1
   * HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version
     * Type REG\_DWORD
     * Value 1

3. **Enable Exchange Online modern authentication**. In order for Windows-based Outlook clients to use modern authentication, Exchange Online must be modern authentication-enabled as well. If modern authentication is disabled for Exchange Online, Windows-based Outlook clients that support modern authentication \(Outlook 2013 or later\) will use basic authentication to connect to Exchange Online mailboxes.

   SharePoint Online is enabled for modern authentication default. For directories created after August 1, 2017, modern authentication is enabled by default in Exchange Online. However, if you had previously disabled modern authentication or if you are using a directory created prior to this date, you will need to manually enable modern authentication.

4. **Enable Skype for Business Online modern authentication**. To prevent legacy authentication requests made by Skype for Business, it's necessary to enable modern authentication for Skype for Business Online. For directories created after August 1, 2017, modern authentication for Skype for Business is enabled by default. We suggest you transition to Microsoft Teams, which supports modern authentication by default.
5. **Block legacy authentication on your mobile device applications**. Applications on your mobile device need to block legacy authentication as well. We recommend using Outlook for Mobile. Outlook for Mobile supports modern authentication by default and will satisfy other MFA baseline protection policies.



## Explore and implement password alternatives

100 XP

* 5 minutes

Since an average of one in every 250 corporate accounts is compromised each month, we know that relying on passwords isn’t a good enterprise defense strategy. As companies continue to add more business applications to their portfolios, the cost of passwords only goes up. In fact, companies are dedicating 30 to 60 percent of their support desk calls to password resets. Given how ineffective passwords can be, it’s surprising how many companies haven’t turned on multi-factor authentication \(MFA\) for their customers or employees.

![Your password doesn&apos;t matter, but MFA does](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/password-multi-factor-authentication.png)

Password-less authentication is a form of multi-factor authentication that replaces the password with a secure alternative. This type of authentication requires two or more verification factors to sign in and are secured with a cryptographic key pair. The device creates a public and private key when registered. The private key can only be unlocked using a local gesture such as a biometric or PIN. Users have the option to either sign in directly via biometric recognition—such as fingerprint scan, facial recognition, or iris scan—or with a PIN that’s locked and secured on the device.

Microsoft Authenticator supports push notifications, one-time passcodes, and biometrics for any Azure AD-connected app and is free to download from the Apple and Android app stores. It also supports passwordless authentication \(in preview\). Windows Hello and Hello for Business are other secure and convenient options \(both require Windows 10\).

![Microsoft&apos;s password replacement offerings](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/password-replacement-offerings.png)

Passwordless technology is here—and users are adopting it as the best experience for strong authentication. More than over 150 million people are already signing in using passwordless methods each month. According to our recent survey, the use of biometrics for work accounts is set to double this year, with nearly a quarter of companies already using or planning to deploy biometrics soon, signaling an increased desire to ditch the archaic password system.

![Microsoft&apos;s passwordless strategy](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-authentication/media/passwordless-strategy.png)

Whether you’re ready to roll out a passwordless authentication strategy today or in a few years, these steps will help get your organization ready:

1. **Develop password-replacement offerings**. Deploy alternatives that coexist with passwords, such as Windows Hello for Business and FIDO. While these offerings coexist with passwords, some workflows and applications will still require passwords. This early stage is about deploying an alternative and getting users used to it.
2. **Reduce user visible password-surface area**. User environments and workflows need to stop asking for passwords. This includes the entire lifecycle of a user’s identity.
   * A user's identity lifecycle includes such steps as provisioning of an account, setting up a brand-new device, using the account/device to access apps and websites, and recovery.
   * Workflows need to ensure these steps work with password-replacements.
   * The goal is to create an environment where the user knows they have a password but never has to use it, thereby helping to decondition users from providing a password every time a password prompt shows on their computer, which is how passwords are phished.
3. **Transition to passwordless deployment**. Once user-visible password surfaces have been eliminated, the next step is for organizations to transition to passwordless deployment where users never type, change, or even know their passwords. This means deploying policies so that users never see the password credential provider on Windows, not in the out-of-box-experience \(OOBE\), not on sign-on, and not in settings. The user signs on to Windows 10 using Windows Hello for Business and enjoys single sign-on to Azure and Active Directory. If the user is forced to authenticate, they use Windows Hello for Business or FIDO.
4. **Eliminate passwords from the identity directory**. This final step entails deleting passwords from the identity directory so they simply do not exist.



## Summary

100 XP

* 1 minute

In this module, you learned about modern authentication and the security benefits it provides to your organization, such as enabling multi-factor authentication and a passwordless environment.

Now that you have completed this module, you should be able to:

* Define modern authentication.
* Understand how to enable multi-factor authentication.
* Explain how passwordless authentication improves security.



