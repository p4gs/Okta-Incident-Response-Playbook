# Okta Incident Response Playbook
A generic security incident response playbook investigating and responding to potential compromises of Okta's internal systems, in the context of a customer or partner of Okta that uses their platform.

## Investigate
- [ ] Review "user.session.impersonation.grant" events in Okta System Logs for signs of unusual or unauthorized access

### If AWS is integrated with Okta SSO
- [ ] Identify all IAM Users and associated active IAM keys used for Okta SSO AWS integration
- [ ] Search AWS CloudTrail logs for unusual activity associated with IAM permissions granted to IAM Users used for Okta SSO integration
</details>
