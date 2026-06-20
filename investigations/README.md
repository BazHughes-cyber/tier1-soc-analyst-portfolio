# Phishing Email Investigation

## Disclaimer

This investigation is an original educational case study created to demonstrate phishing email analysis techniques and SOC investigation methodology. It does not reproduce proprietary training materials, challenge answers, or examination content.

---

# Executive Summary

A user reported an email claiming to be from Microsoft's Security Team regarding unusual sign-in activity on their account. The purpose of this investigation was to determine whether the email was legitimate or part of a phishing campaign.

Analysis of the sender domain, email content, and embedded URL identified several indicators commonly associated with phishing attacks. The email attempted to create a sense of urgency and directed the recipient to a fraudulent website designed to mimic a legitimate Microsoft login page.

The email was classified as a phishing attempt and appropriate mitigation actions were recommended.

---

# Alert Details

| Field             | Value              |
| ----------------- | ------------------ |
| Alert Type        | Suspicious Email   |
| Severity          | Medium             |
| Reported By       | End User           |
| Date Investigated | 21 June 2026       |
| Status            | Confirmed Phishing |

---

# Email Information

## Sender

[notifications@micr0soft-support.com](mailto:notifications@micr0soft-support.com)

## Subject

Urgent: Unusual Sign-in Activity Detected

## Recipient

[employee@company.com](mailto:employee@company.com)

## Source IP

185.203.118.77

---

# Investigation Process

## Step 1: Header Analysis

The email header indicated that the message originated from the domain:

micr0soft-support.com

The domain appears designed to impersonate Microsoft by replacing the letter "o" with the number "0".

This technique is commonly referred to as a lookalike or typosquatting domain.

### Finding

Suspicious sender domain identified.

---

## Step 2: Sender Verification

The sender claimed to represent Microsoft's Security Team.

However, legitimate Microsoft security notifications would typically originate from Microsoft-owned domains rather than a third-party domain.

### Finding

Sender identity could not be verified and did not align with the claimed organisation.

---

## Step 3: Content Analysis

The email contained language intended to pressure the recipient into taking immediate action.

Examples included:

* "Urgent"
* "Verify your account immediately"
* "within 24 hours"

These phrases are commonly used in phishing campaigns to create urgency and reduce critical thinking by the recipient.

### Finding

Social engineering techniques identified.

---

## Step 4: URL Analysis

The embedded hyperlink directed users to:

http://microsoft-security-verification.com/login

The URL does not belong to Microsoft.

Indicators of concern include:

* Use of HTTP rather than HTTPS
* Domain unrelated to Microsoft
* Credential harvesting theme

### Finding

Embedded URL appears malicious and intended to capture user credentials.

---

# Indicators of Compromise (IOCs)

## Domains

micr0soft-support.com

microsoft-security-verification.com

## IP Address

185.203.118.77

## Subject Line

Urgent: Unusual Sign-in Activity Detected

---

# MITRE ATT&CK Mapping

## T1566 - Phishing

The attacker attempted to gain access to user credentials through a fraudulent email designed to impersonate a trusted organisation.

---

# Risk Assessment

Likelihood: High

Impact: Medium

If a user were to interact with the phishing site and enter credentials, an attacker could gain unauthorised access to corporate resources, email accounts, and potentially facilitate further compromise.

Overall Risk Rating: High

---

# Conclusion

The investigation determined that the email was a phishing attempt.

Multiple indicators supported this assessment, including a lookalike sender domain, social engineering language, and a suspicious external URL designed to imitate a legitimate Microsoft service.

No evidence was found to suggest the email originated from a trusted Microsoft source.

---

# Recommendations

1. Block the sender domain at the email gateway.
2. Block access to the identified malicious domains.
3. Notify affected users of the phishing attempt.
4. Conduct awareness training covering phishing indicators.
5. Monitor authentication logs for suspicious login activity.
6. Implement multi-factor authentication where possible.
7. Report the domains to relevant threat intelligence platforms.

---

# Analyst Notes

This investigation demonstrates standard Tier 1 SOC analyst procedures including:

* Email triage
* Header analysis
* IOC identification
* Risk assessment
* MITRE ATT&CK mapping
* Incident reporting

