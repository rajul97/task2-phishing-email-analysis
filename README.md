# Task 2 - Phishing Email Analysis

## Objective
Analyze a suspicious email to identify phishing indicators in both the email body and header information.  
The aim is to detect signs of spoofing, malicious links, urgent language, and authentication failures.

---

## Tools Used
- **MXToolbox Email Header Analyzer** → https://mxtoolbox.com/EmailHeaders.aspx
- **Manual Link Inspection** (hover over links without clicking)
- **Basic Grammar & Content Review**

---

## Email Body Indicators
| Indicator | Why It’s Suspicious | Example |
|-----------|--------------------|---------|
| **Spoofed sender domain** | Uses `paypa1.com` instead of `paypal.com` (number substitution) | support@paypa1.com |
| **Urgent tone** | Creates fear and pushes immediate action | "Your account will be suspended in 24 hours" |
| **Mismatched URL** | Link text says “Verify Now” but leads to a fake domain | `http://secure-paypa1.com/account-update` |
| **Grammar errors** | Poor sentence structure indicates low credibility | "account is on suspended" |
| **Unusual domain** | Domain not owned by PayPal | secure-paypa1.com |

---

## Email Header Analysis
*(Header file: `email_headers.txt`)*

| Header Field | Observation | Risk |
|--------------|-------------|------|
| SPF | **Fail** | Sender IP not authorized for domain → spoofing |
| DKIM | **Fail** | Missing/invalid signature → content could be altered |
| DMARC | **Fail** | Domain policy not enforced → easier spoofing |
| Return-Path | `paypa1.com` instead of official PayPal domain | Fake sender |
| Received IP | 197.210.45.123 (Nigeria) | Geographic mismatch with PayPal’s servers |

---

## Phishing Indicators Summary
- Fake sender domain designed to look legitimate.
- Urgent request with short deadline to provoke action.
- Mismatched link text and actual URL.
- Poor grammar and spelling errors.
- SPF/DKIM/DMARC authentication failures.
- Email originated from an unusual geographic location.

---

## Conclusion
This is a **phishing attempt** using:
- **Email spoofing** to fake the sender.
- **Social engineering** with urgency to manipulate the recipient.
- **Malicious link redirection** to steal credentials.

The recipient should not click on any links, open attachments, or reply to the sender.

---

## Recommended Actions
1. **Do not click** on any links or open attachments.
2. Report the email to PayPal at `phishing@paypal.com`.
3. Mark the email as spam/phishing in the email client.
4. Educate the user on recognizing urgent, suspicious emails.
5. Use email header analysis tools for future suspicious messages.

---

**Author:** Rajul Gupta  
**Date:** 15 August 2025  
**Purpose:** Cyber Security Internship Task Submission
