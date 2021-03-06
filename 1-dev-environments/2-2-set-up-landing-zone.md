# 2. Set Up Initial Landing Zone Using AWS Control Tower

In this step your Cloud Administrators will use the AWS Control Tower service in your new AWS master account to establish an initial “landing zone” or a foundation of security guardrails and other resources that will help your organization manage use of the AWS platform. You can learn more by reviewing [AWS Control Tower Features](https://aws.amazon.com/controltower/features/).

This step should take about 90 minutes to complete.

1. [Log In as Administrator IAM User](#1-log-in-as-administrator-iam-user)
2. [Create Landing Zone Using AWS Control Tower](#2-create-landing-zone-using-aws-control-tower)
3. [Set AWS Account Root User Password and Enable MFA](#3-set-aws-account-root-user-password-and-enable-mfa)
4. [Log In Via Control Tower Administrator User](#4-log-in-via-control-tower-administrator-user)
5. [Configure Multi-Factor Authentication (MFA) Requirements](#5-configure-multi-factor-authentication-mfa-requirements)
6. [Enable MFA via AWS SSO for Control Tower Administrator User](#6-enable-mfa-via-aws-sso-for-control-tower-administrator-user)
7. [Receive and Process AWS Email Messages](#7-receive-and-process-aws-email-messages)
8. [Review AWS Control Tower Best Practices for Administrators](#8-review-aws-control-tower-best-practices-for-administrators)

## 1. Log In as Administrator IAM User

Log in as the Administrator IAM user that you created in the last section before you use AWS Control Tower to set up your initial landing zone.

## 2. Create Landing Zone Using AWS Control Tower

Before using AWS Control Tower to create an initial landing zone, ensure that you review these considerations:

* **Desired Home AWS Region** - Ensure that you select the proper AWS region in the upper right hand side of the AWS Management Console before creating the landing zone. The AWS region you select should be the AWS region in which you expect do perform the majority of your work with AWS and from which you will maintain your foundation.
* **Email Distribution Lists** - Consult the [set of AWS account root user email addresses](1-4-address-prerequisites.md#1-create-email-addresses-for-new-aws-accounts) that you established earlier.
* **Pre-Launch Checks** - Since you’ve just created a new master AWS account, the pre-launch check considerations for creating your landing zone should already be met.

Follow the steps in [Getting Started with AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/getting-started-with-control-tower.html) to set up your landing zone. 

The set up process can take 20-60 minutes to complete.

## 3. Set AWS Account Root User Password and Enable MFA

Since AWS Control Tower creates two new member accounts while setting up the initial landing zone, you should follow AWS security best practices by setting the password and enabling MFA for the root user of each of the following accounts:

* Audit
* Log archive

See [Log In as Root User](https://docs.aws.amazon.com/controltower/latest/userguide/best-practices.html#root-login) in the AWS Control Tower documentation for instructions to set the root user’s password.

See [Enable MFA on the AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html#id_root-user_manage_mfa) for instructions to enable MFA.

## 4. Log In Via Control Tower Administrator User

As part of the landing zone set up, AWS Control Tower creates a Control Tower Administrator user in the AWS Single-Sign On ( AWS SSO) service in your master account. 

The email address associated with the AWS master account’s root user will receive an email message containing an invite to activate the Control Tower Administrator user account.  Review the invitation and accept it.

<img src="../images/accept-aws-sso-invitation.png" alt="Accept SSO Invitation" width="400"/>

When accepting the invite, you will be directed to set the password for the Control Tower Administrator user.

The email message you recieved contains a portal URL that you should bookmark given that it will be used by human users to access your new AWS accounts.

## 5. Configure Multi-Factor Authentication (MFA) Requirements

Before adding any human users to AWS SSO and enabling the users to access your AWS environment in later sections, it's a best practice to configure AWS SSO to require multi-factor authentication (MFA).

In the following steps, you will modify your AWS SSO configuration to align with typical security best practices.

1. Since you just set the password for the **`Control Tower Administrator`** user, you should already be logged into the AWS SSO portal.
2. From within the portal, select **`AWS Account`** icon to expand the current list of AWS accounts.
3. Select the AWS **master** account.
4. Select **`Management console`** associated with the **`AWSAdministratorAccess`** role.
5. Select the appropriate AWS region.
6. Navigate to **`AWS Single Sign-on`**.
7. Select **`Settings`** in AWS SSO.
8. Under **`Multifactor authentication`** select **`Configure`**.
9. Under **`Users should be prompted for multi-factor authentication (MFA)`**, select **`Every time they sign in (always-on)`**.
10. Under **`When prompted for a MFA code` select `Require them to provide a one-time password sent by email`**.
11. Under **`Who can manage MFA devices` select `Users and administrators can add and manage MFA devices`**.
12. Select **`Save changes`**.

---
**Note: Auditing use of MFA**

The configuration shown above does not force the use of MFA, but it does impose an additional overhead of a one-time password sent via email for users that have not yet registered an MFA device.

You will likely want to establish either manual or automatic recurring audits to ensure that your users have registered an MFA device.

---

## 6. Enable MFA via AWS SSO for Control Tower Administrator User

Follow the instruction in [How to Register a Device for Use with Multi-Factor Authentication](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-device-registration.html).

## 7. Receive and Process AWS Email Messages

### AWS Organizations Email Verification Request

You will receive one more email with subject AWS Organizations email verification request to the master account email address. Click on Verify your email address to continue with inviting newly created accounts into AWS Organization.

### AWS Notification Email Messages for Each Region

The email address you provided for the audit account will receive AWS Notification - Subscription Confirmation emails from every AWS Region supported by AWS Control Tower. To receive compliance emails in your audit account, you must choose the Confirm subscription link within each email from each AWS Region supported by AWS Control Tower.

## 8. Review AWS Control Tower Best Practices for Administrators

Now that you've set up your initial landing zone, take a few minutes to review [Best Practices for Account Administrators](https://docs.aws.amazon.com/controltower/latest/userguide/best-practices.html#tips-for-admin-maint) so that you understand temporary limitations and other considerations when working with AWS Control Tower.

For example:

* **Managing Organizational Units (OUs)** - AWS Control Tower currently supports only a single level of AWS Organizations Organizational Units (OUs) and creation of OUs to be used with AWS accounts managed by AWS Control Tower must be performed via AWS Control Tower and not via AWS Organizations.
* **Modification of AWS Account Root User Email Addresses** - AWS Control Tower does not currently support self-service modification of the email addresses associated with the root user of each AWS account.  You currently need to contact AWS Support to have these email addresses changed.

 ## Next Steps
[3. Set Up Initial AWS Platform Access Controls](2-3-set-up-aws-platform-access-controls.md)
