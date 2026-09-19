# Phishing Email Analysis Report

## 1. Executive Summary

A synthetic phishing email was examined using a controlled, non-interactive analysis workflow. The message contains multiple indicators commonly associated with phishing, including a look-alike sender domain, a matching Reply-To domain, failed authentication results, a suspicious verification hostname, and an urgent account-suspension message.

The analysis did not access the embedded URL or any external phishing infrastructure.

## 2. Sample

Sample: `samples/phishing-example.eml`

The message is intentionally synthetic. It uses `.example` domains and the TEST-NET-3 address `203.0.113.50`.

## 3. Header Findings

| Field | Observation |
|---|---|
| From | `security-alert@micr0soft-support.example` |
| Reply-To | `verify-account@micr0soft-support.example` |
| Message-ID | `<20260919081522.12345@micr0soft-support.example>` |
| Received | From `mail.micr0soft-support.example (203.0.113.50)` |
| SPF | FAIL |
| DKIM | FAIL |
| DMARC | FAIL |

## 4. URL Findings

The message contains:

`https://login-microsoft-account.example/verify`

Static parsing identifies:

- Scheme: HTTPS
- Host: `login-microsoft-account.example`
- Path: `/verify`

The hostname does not use a Microsoft production domain. In this laboratory sample, however, the hostname is intentionally under `.example`, so this observation is about the constructed sample and is not a live domain-ownership finding.

## 5. IOC Findings

### Email Addresses

- `security-alert@micr0soft-support.example`
- `verify-account@micr0soft-support.example`

### Domains

- `micr0soft-support.example`
- `mail.micr0soft-support.example`
- `login-microsoft-account.example`

### IP Address

- `203.0.113.50`

### URL

- `https://login-microsoft-account.example/verify`

## 6. Behavioral Indicators

The email attempts to create urgency by stating that the account will be suspended within 24 hours unless the recipient verifies their identity.

The sender also uses the look-alike string `micr0soft`, where a zero replaces the expected letter `o`.

## 7. Assessment

The combination of brand impersonation, urgency, failed authentication results, and a non-brand verification hostname provides a coherent set of phishing indicators within the synthetic sample.

This assessment is limited to the supplied message. It does not establish the identity of a real sender, infrastructure ownership, malware presence, or a real-world campaign.

## 8. Evidence

- `evidence/01-ioc-extraction.txt`
- `evidence/02-url-analysis.txt`
- `evidence/03-ioc-list.txt`
- `screenshots/01-email-sample-and-headers.png`
- `screenshots/02-ioc-extraction.png`
- `screenshots/03-url-static-analysis.png`
- `screenshots/04-ioc-list.png`

## 9. Recommended Analyst Handling

For a real suspicious email, an analyst should avoid clicking unknown links or opening unexpected attachments, preserve the original message and headers, extract indicators safely, and submit relevant evidence through the organization's established security-reporting process.

## 10. Limitations

This project intentionally excludes:

- Live URL interaction
- Credential submission
- Attachment detonation
- DNS verification against the Internet
- Attribution
- Live reputation lookups

These limitations are deliberate to keep the exercise controlled and reproducible.
