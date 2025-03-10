IAM Threat Detection and Remediation Lab

Overview

This lab involved detecting, analyzing, and remediating IAM (Identity and Access Management) security threats using Google Cloud Security Command Center (SCC) and Cloud Logging. The goal was to differentiate between normal and malicious IAM activity by granting permissions, investigating findings, and taking corrective action.

Objectives

Trigger an IAM threat detection by granting project owner rights to an external account.

Access and analyze findings in the Security Command Center to determine normal vs. malicious activity.

Investigate security logs in Cloud Logging to gather additional details about the threat.

Remediate the threat by revoking unauthorized access.

Tasks Performed

1. Granting Permissions to an External Account
Assigned the Owner role to an external user (bad.actor.demo@gmail.com) via the IAM settings.
This action triggered an Event Threat Detection finding, as granting project owner access to an external entity is considered a security risk.

2. Accessing IAM Threat Findings
Opened Security Command Center (SCC) to review threat findings.
Used filters to isolate findings related to Persistence: IAM Anomalous Grant events.
Identified two IAM findings:
One was normal (a system-generated grant to a user within the qwiklabs.net organization).
One was malicious (granting ownership to an external user).

3. Analyzing the Findings
Checked the Principal Email field in SCC to identify which account granted the permissions.
Verified that the malicious finding was associated with bad.actor.demo@gmail.com, confirming unauthorized access.

4. Investigating in Cloud Logging
Used Logs Explorer to analyze IAM logs with the following query:
sql
Copiar
Editar
protoPayload.authorizationInfo.permission="resourcemanager.projects.setIamPolicy"
protoPayload.methodName="InsertProjectOwnershipInvite"
Extracted details including:
The user who performed the action.
The recipient of the permissions.
The IP address and browser user agent, which could help in further investigations.

5. Remediating the Malicious IAM Finding
Revoked the Owner role from bad.actor.demo@gmail.com by:
Navigating to IAM & Admin > IAM
Locating the external user.
Removing their permissions and saving the changes.

Conclusion

Through this lab, I gained hands-on experience with:
✅ IAM threat detection using Security Command Center.
✅ Log analysis using Cloud Logging to trace security incidents.
✅ Incident response by identifying and remediating malicious activity.
