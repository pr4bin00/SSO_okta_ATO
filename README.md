# sso_okta


## Description

A zero-click account takeover vulnerability has been discovered in Spacelift's custom SSO integration using SAML 2.0 with Okta. An attacker can exploit this flaw to gain unauthorized access to another organization's workspace without the victim's interaction, posing a significant threat to user security and data integrity.

## Exploitation

1. Attacker creates an organization (trexif.app.spacelift.dev) and integrates it with a custom SSO login using Okta.

2.Victim has an existing organization (techvictim.app.spacelift.dev) with the email sigdelprabin07@gmail.com.

3.Attacker creates a user in their Okta instance with the victim's email (sigdelprabin07@gmail.com) and sets a password for this account.

4.Attacker invites sigdelprabin07@gmail.com to their organization (trexif.app.spacelift.dev). The victim does not accept this invitation.

5.Attacker logs into trexif.app.spacelift.dev via their custom SSO integration using the victim's email and the password set in Okta.

6.Once logged into the attacker's organization, the attacker gains access to the victim's organization (techvictim.app.spacelift.dev) without requiring any approval or action from the victim.

## PoC
I have provided video  poc below.

## Risk
1.Unauthorized access to victim's organization, including sensitive resources and data.

2.Full control over victim's account within the Spacelift platform.

3.Bypasses victim approval, making it a zero-click attack

## Remediation
The vulnerability arises due to improper validation of user identity between the custom SSO integration and Spacelift's organization membership mechanisms. The system fails to distinguish between identical email identities from different SSO providers.


1.Implement stricter validation of user identities when integrating SSO, ensuring the identity context (e.g., SSO issuer) is verified.

2.Restrict access to organizations unless explicitly approved by the user.

3.Enforce domain-based trust boundaries to prevent cross-organization access through mismatched SSO identities.


## Reference

Same vulnerability exploited :
1. https://rikeshbaniya.medium.com/account-takeover-using-sso-logins-fa35f28a358b
