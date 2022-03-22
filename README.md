# Okta Incident Response Playbook
A generic security incident response playbook for investigating and responding to potential compromises of Okta's internal systems, in the context of a customer or partner of Okta that uses their platform.

## Investigate
- [ ] Review "user.session.impersonation.grant" events in Okta System Logs for signs of unusual or unauthorized access
- [ ] Review Okta system logs for unusual "Reset Password" events
- [ ] Review Okta System logs for unusual "Reset Multifactor" events
- [ ] Review Okta System logs for unusual changes to Multifactor Authentication policies that would make it easier for an attacker to persist access with compromised credentials (e.g. policy deletions, user exceptions, etc.)

### If AWS is integrated with Okta SSO ([example](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Amazon-Web-Service.html?baseAdminUrl=https://rapid7-admin.okta.com&app=amazon_aws&instanceId=0oa197c2qafCHfvnH0h8))
- [ ] Identify all IAM Users and associated active IAM keys used for Okta SSO AWS integration
- [ ] Search AWS CloudTrail logs for unusual activity associated with IAM permissions granted to IAM Users used for Okta SSO integration

## Mitigate
### If AWS is integrated with Okta SSO ([example](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Amazon-Web-Service.html?baseAdminUrl=https://rapid7-admin.okta.com&app=amazon_aws&instanceId=0oa197c2qafCHfvnH0h8))
- [ ] Rotate IAM keys used for Okta SSO integration
- [ ] Apply IP address allowlist rules to IAM policies used by IAM principals ([AWS guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_aws_deny-ip.html)) ([Okta IP allowlist](https://help.okta.com/en/prod/Content/Topics/Security/ip-address-allow-listing.htm))
