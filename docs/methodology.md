# Phishing Email Analysis Methodology

## Objective

The objective is to demonstrate a repeatable workflow for examining a suspicious email while minimizing interaction with potentially malicious content.

## 1. Header Review

The analyst first reviews:

- From
- To
- Subject
- Date
- Message-ID
- Reply-To
- Received
- Authentication-Results

The purpose is to establish the message's visible identity, routing information, and authentication results before examining embedded indicators.

## 2. Authentication Review

The sample contains explicit authentication results:

- SPF: FAIL
- DKIM: FAIL
- DMARC: FAIL

These values are treated as observations from the synthetic message rather than independently verified DNS or mail-server results.

## 3. IOC Extraction

Indicators are extracted without contacting the embedded URL. The workflow records:

- Email addresses
- Domains
- IP addresses
- URLs
- Authentication results
- Notable textual indicators

The extracted values are preserved in `evidence/` and normalized in `iocs/ioc-list.txt`.

## 4. URL Static Analysis

The embedded URL is parsed into components:

- Scheme
- Host
- Path

The analysis compares the claimed brand in the message with the hostname used by the synthetic sample. No request is sent to the URL.

## 5. Evidence Preservation

Each major analysis stage has a corresponding evidence file and screenshot. This provides a traceable relationship between the observed data, the analyst's commands, and the final report.

## 6. Reporting

The final report distinguishes:

- Direct observations from the sample
- Analytical interpretation
- Safety and environmental limitations

Because the sample is synthetic, conclusions are limited to the constructed message and do not establish attribution to a real actor or campaign.
