# Okta Incident Response Playbook
A generic security incident response playbook for investigating and responding to potential compromises of Okta's internal systems, in the context of a customer or partner of Okta that uses their platform.

## Investigate
|Action Item|Event Types to Analyze|
|------------- |-------------|
|<ul><li>- [ ] Review Okta System logs for unusual "Impersonation" events</li></ul>|<ul><li>- [ ] user.session.impersonation.grant</li><li>- [ ] user.session.impersonation.initiated</li></ul>|
|<ul><li>- [ ] Review Okta system logs for unusual "Reset Password" events</li></ul>|<ul><li>- [ ] user.account.reset_password</li></ul>|
|<ul><li>- [ ] Review Okta System logs for unusual "Reset Multifactor" events|<ul><li>- [ ] user.mfa.factor.update</li><li>- [ ] system.mfa.factor.deactivate</li><li>- [ ] user.mfa.attempt_bypass</li></ul>|
|<ul><li>- [ ] Search email system logs for notifications about "Reset Password" and "Reset Multifactor" events and correlate them with corresponding Okta events analyzed based on playbook steps listed above.</li></ul> *NOTE:* In the event an attacker was able to tamper with Okta's system logs, this will provide independent validation about when and for whom these events occurred.||
|<ul><li>- [ ] Review Okta System logs for unusual changes to Multifactor Authentication policies that would make it easier for an attacker to persist access with compromised credentials (e.g. policy deletions, user exceptions, etc.)||

### If AWS is integrated with Okta SSO ([example](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Amazon-Web-Service.html?baseAdminUrl=https://rapid7-admin.okta.com&app=amazon_aws&instanceId=0oa197c2qafCHfvnH0h8))
- [ ] Identify all IAM Users and associated active IAM keys used for Okta SSO AWS integration
- [ ] Search AWS CloudTrail logs for unusual activity associated with IAM permissions granted to IAM Users used for Okta SSO integration

### References
* [eshlomo1's Microsoft Sentinel 4 SecOps Okta Events of Interest](https://github.com/eshlomo1/Microsoft-Sentinel-4-SecOps/blob/master/OKTA/Security-Events/Okta-Security-Event.md)
* [Okta System Log Event Types](https://developer.okta.com/docs/reference/api/event-types/)

## Mitigate
### If AWS is integrated with Okta SSO ([example](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Amazon-Web-Service.html?baseAdminUrl=https://rapid7-admin.okta.com&app=amazon_aws&instanceId=0oa197c2qafCHfvnH0h8))
- [ ] Rotate IAM keys used for Okta SSO integration
- [ ] Apply IP address allowlist rules to IAM policies used by IAM principals ([AWS guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_aws_deny-ip.html)) ([Okta IP allowlist](https://help.okta.com/en/prod/Content/Topics/Security/ip-address-allow-listing.htm))
