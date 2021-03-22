# Enable identity protection in Azure Active Directory

## Introduction to identity protection

100 XP

* 2 minutes

### Change behaviors to support identity protection <a id="change-behaviors-to-support-identity-protection"></a>

Azure Active Directory \(AD\) Identity Protection is a tool that allows organizations to:

* Automate the detection and remediation of identity-based risks.
* Investigate risks using data in the portal.
* Export risk detection data to third-party utilities for further analysis.

![New risky users detected screen image](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/identity-protection.png)

Identity Protection uses what Microsoft has learned from Azure AD, Microsoft accounts, and Xbox customers to protect users. Microsoft analyzes 6.5 trillion signals per day to identify and protect customers from threats.

With Azure Active Directory Identity Protection policies, you can:

* Require users to register for Azure multi-factor authentication \(MFA\).
* Automate remediation of risky sign-ins and compromised users through Azure MFA and self-service password reset.

All Identity Protection policies impact the sign-in experience for users. Allowing users to register for and use tools like Azure MFA and self-service password reset reduce that impact. These tools along with the appropriate policy choices gives users a self-remediation option when they need it.  


## Build security best practices into user experience

100 XP

* 13 minutes

Enabling the Identity Protection policy requiring multi-factor authentication registration and then targeting all users ensures they can use Azure MFA to self-remediate in the future. Configuring this policy provides users a 14-day period to register. At the end of the 14-day period, all users are required to register.

To enable the policy:

1. Open the Azure AD Identity Protection blade in the Azure portal, and select **MFA registration policy**:

   ![Azure AD Identity Protection blade in the Azure portal MFA registration policy selected](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/mfa-registration-policy.png)

2. By default, the Access control to require MFA registration will be enabled. Leave this option selected.

   ![Select controls to be enforced is selected](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/access.png)

3. Select **On** under **Enforce Policy** to require users to register for MFA.

   ![Enforce policy is turned on](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/enforce-policy.png)

At sign-in to any Azure AD-integrated application, the user gets a notification about the requirement to set up the account for multi-factor authentication. This policy is also triggered in the Windows 10 Out-of-Box Experience for new users with a new device.

![User gets a notification about the requirement to set up the account for multi-factor authentication.](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/microsoft-azure.png)

An administrator can configure a policy for sign-in risks in the Azure AD Identity Protection blade, which requires users to verify their identity through MFA.

![Sign-in risk policy page](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/sign-in-risk-policy.png)

### The user experience <a id="the-user-experience"></a>

Affected users are notified when they try to sign in and trigger a policy, for example, when the user is informed that something unusual was detected about their sign-in, such as signing in from a new location, device, or app.

![Help us protect your account screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/protect.png)

The user is then required to prove their identity by completing Azure MFA with one of their previously registered methods.

### Forcing password changes <a id="forcing-password-changes"></a>

User risk policies in Azure AD Identity Protection allow you to require a password change based on risk.

![User risk policies in Azure AD Identity Protection screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/user-risk-policy.png)

To improve the experience, you can enable self-service password reset so users can complete this process without help desk involvement. In the Azure Active Directory portal, you can configure self-service password reset for no one, a set of Azure AD groups, or the entire organization.

![Password reset screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/password-reset.png)

Then, when a user affected by the user risk policy is informed that their account security is at risk because of suspicious activity or leaked credentials, they are prompted to prove their identity though Azure MFA and forced to change their password.

![Your account security is at risk screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/at-risk.png)

Both sign-in and user Azure AD Identity Protection risk policies allow the configuration of risk levels that trigger the additional verifications noted above. Risk levels in Identity Protection are based on the precision of the detection and powered by Microsoft’s machine learning. To customize what experience users are presented, administrators can include/exclude certain users/groups from the User Risk and Sign-In Risk Policies. Administrators cannot change what “triggers” result in high, medium, or low risks.

![Sign-in risk screen set to High](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/conditions.png)

Now that you’ve read about creating security best practices, let’s walk through the experience of enabling a combined multi-factor authentication and self-service password reset registration for your end users.

#### Explore how to enable a combined MFA and SSPR registration experience in Azure AD <a id="explore-how-to-enable-a-combined-mfa-and-sspr-registration-experience-in-azure-ad"></a>

View a [video version](https://www.microsoft.com/videoplayer/embed/RE4C7zQ) of the interactive guide \(captions available in more languages\).

[![Enable a combined MFA and SSPR registration experience in Azure AD](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/interactive-multi-factor-authentication-registration.png)](https://mslearn.cloudguides.com/guides/Enable%20a%20combined%20MFA%20and%20SSPR%20registration%20experience%20in%20Azure%20AD)

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.  
Incorporate identity into your development approach

100 XP

* 10 minutes

Signals generated by and fed to Identity Protection can be further fed into tools like Conditional Access to make access decisions or fed back to a security information and event management \(SIEM\) tool for further investigation based on your organization's enforced policies. Microsoft Graph APIs also allow organizations to collect data from Identity Protection for further processing.

Microsoft Graph is the Microsoft unified API endpoint and the home of Azure Active Directory Identity Protection APIs. There are three APIs that expose information about risky users and sign-ins.

* The first API, **riskDetection**, allows you to query Microsoft Graph for a list of both user and sign-in linked risk detections.
* The second API, **riskyUsers**, allows you to query Microsoft Graph for information about users that Identity Protection detected as risky.
* The third API, **sign in**, allows you to query Microsoft Graph for information on sign-ins with specific properties related to risk state, detail, and level.

To query Identity Protection APIs, an application must be created within Azure AD with the appropriate permissions:

1. Start by registering an application:

   ![Registering an application screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/register.png)

2. Select API permissions under the newly registered application. Select **Microsoft Graph and Application permissions**. Then select the **IdentityRiskEvent.Read.All permission**:

   ![Microsoft Graph and Application permissions screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/application-permissions.png)

3. Once the permissions are provided to the application, select **Certificates & secrets** and create a new **client secret** with **1 year** expiration.

   ![Add a client secret screen](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/aadip-risk-event.png)

With the information collected from these steps, you can now collect information on the Azure AD Identity Protection events of your users. The following script is a sample PowerShell script for collecting identity risk detections:Azure PowerShellCopy

```text
$ClientID       = "<your client ID here>"        # Should be a ~36 hex character string; insert your info here
$ClientSecret   = "<your client secret here>"    # Should be a ~44 character string; insert your info here
$tenantdomain   = "<your tenant domain here>"    # For example, contoso.onmicrosoft.com

$loginURL       = "https://login.microsoft.com"
$resource       = "https://graph.microsoft.com"

$body       = @{grant_type="client_credentials";resource=$resource;client_id=$ClientID;client_secret=$ClientSecret}
$oauth      = Invoke-RestMethod -Method Post -Uri $loginURL/$tenantdomain/oauth2/token?api-version=1.0 -Body $body

Write-Output $oauth

if ($oauth.access_token -ne $null) {
        $headerParams = @{'Authorization'="$($oauth.token_type) $($oauth.access_token)"}

        $url = "https://graph.microsoft.com/beta/identityRiskEvents"
        Write-Output $url

        $myReport = (Invoke-WebRequest -UseBasicParsing -Headers $headerParams -Uri $url)

        foreach ($event in ($myReport.Content | ConvertFrom-Json).value) {
            Write-Output $event
        }

} else {
        Write-Host "ERROR: No Access Token"
}
```

You can also use the Microsoft Graph Explorer to query the same information. When you first sign in to the Graph Explorer, you're required to accept permissions to run queries. If you had previously accepted the permissions, you can find the new IdentityRiskEvent read permissions under Modify permissions.

![Microsoft Graph Explorer screen for querying the same information](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/modify-positions.png)

Once you've approved the permissions for Azure AD Identity Protection APIs provided to the previously created application, you can run a query to pull the API data. For example, selecting **Get, beta**, and typing [**https://graph.microsoft.com/beta/riskDetections**](https://graph.microsoft.com/beta/riskDetections) provides all the risk detections that Azure AD Identity Protection has discovered.

![Once you have approved the permissions for Azure AD Identity Protection APIs provided to the previously created application, you can run a query to pull the API data.](https://docs.microsoft.com/en-gb/learn/m365/m365-identity-cultural-shift/media/request-body.png)

The following sections provide two sample scenarios and queries you can use.

#### Get offline risk detections \(riskDetection API\) <a id="get-offline-risk-detections-riskdetection-api"></a>

With Identity Protection sign-in risk policies, you can apply conditions when risk is detected in real time. But what about detections that are discovered offline? To understand what detections occurred offline, and would not have triggered the sign-in risk policy, you can query the riskDetection API.

`GET https://graph.microsoft.com/beta/riskDetections?$filter=detectionTimingType eq 'offline'`

#### Get users who successfully passed an MFA challenge triggered by a risky sign-in policy \(riskyUsers API\) <a id="get-users-who-successfully-passed-an-mfa-challenge-triggered-by-a-risky-sign-in-policy-riskyusers-api"></a>

To understand the impact Identity Protection risk-based policies have on your organization, you can query all the users who successfully passed an MFA challenge triggered by a risky sign-in policy. This information can help you understand which users Identity Protection may have falsely detected as at risk and which of your legitimate users may be performing actions that the AI deems risky.

`GET https://graph.microsoft.com/beta/riskyUsers?$filter=riskDetail eq 'userPassedMFADrivenByRiskBasedPolicy'`  




## Summary

100 XP

* 1 minute

In this module, you learned about Azure Active Directory \(AD\) Identity Protection and ways to optimize the end-user experience while benefiting security.

Now that you have completed this module, you should be able to:

* Describe Azure AD Identity Protection.
* List the Azure AD Identity Protection support for development tools.
* Explain how users can remediate risky behavior.

