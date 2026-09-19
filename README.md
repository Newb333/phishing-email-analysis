# Phishing Email Analysis Lab

A controlled phishing email analysis lab covering email headers, SPF/DKIM/DMARC authentication, URL inspection, IOC extraction, and forensic reporting.

## Scope

This project analyzes a synthetic phishing email in an isolated, documentation-only context.

The sample uses:

- `.example` hostnames rather than real production domains
- TEST-NET-3 address `203.0.113.50`
- No real credential collection or external infrastructure

## Analysis Workflow

1. Review the email body and message headers.
2. Extract sender, Reply-To, Message-ID, Received, authentication results, URLs, domains, and IP addresses.
3. Perform static URL analysis without visiting the destination.
4. Build a normalized IOC list.
5. Document observations and limitations in a forensic-style report.

## Repository Structure

```text
phishing-email-analysis/
├── samples/
│   └── phishing-example.eml
├── headers/
├── iocs/
│   └── ioc-list.txt
├── evidence/
│   ├── 01-ioc-extraction.txt
│   ├── 02-url-analysis.txt
│   └── 03-ioc-list.txt
├── screenshots/
│   ├── 01-email-sample-and-headers.png
│   ├── 02-ioc-extraction.png
│   ├── 03-url-static-analysis.png
│   └── 04-ioc-list.png
├── reports/
│   └── Phishing_Email_Analysis_Report.md
├── docs/
│   └── methodology.md
└── README.md
```

## Key Observations

The synthetic message contains several phishing indicators:

- A sender domain using the look-alike string `micr0soft`.
- A Reply-To address on the same look-alike domain.
- SPF, DKIM, and DMARC results explicitly marked as FAIL in the synthetic headers.
- A verification URL hosted on a non-brand `.example` hostname.
- Urgency created by a 24-hour account-suspension threat.

These observations describe the constructed sample and should not be interpreted as evidence about any real Microsoft infrastructure.

## Evidence

Screenshots and extracted evidence are retained in the repository so the analysis can be reproduced and reviewed.

## Documentation

- [Methodology](docs/methodology.md) — analysis workflow and evidence-preservation process.
- [Final Report](reports/Phishing_Email_Analysis_Report.md) — consolidated findings, indicators, limitations, and analyst handling.

## Safety

This lab intentionally avoids interacting with live phishing infrastructure. The URL is analyzed as text only, and the sample uses reserved/documentation namespaces.

## Disclaimer

This project is for cybersecurity education, portfolio demonstration, and controlled laboratory analysis. It does not represent an investigation of a real phishing campaign.
