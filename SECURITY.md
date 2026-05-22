# Security Policy

## Supported Versions

This project is a proof-of-concept (POC) and is not actively maintained. 
It is intended for research and educational purposes only.

| Version | Supported          |
| ------- | ------------------ |
| master  | ✅ (POC only)      |

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please follow 
these steps:

1. **Do not** open a public GitHub Issue with exploit details.
2. Instead, email the maintainer directly or open a GitHub Issue with a general description only (no exploit code or payload).
3. Allow up to 30 days for a response before any public disclosure.

## Security Considerations

This tool is designed to **detect** SQL Injection and XSS attacks — it is not designed to be deployed as a production-grade firewall. Known limitations include:

- The neural network is trained on a fixed dataset and may not generalise to novel attack patterns.
- No input sanitisation is applied to the HTTP traffic loader itself.
- The saved model file (`/tmp/ann.db`) has no integrity verification and should not be used in untrusted environments.

## Disclaimer

This project is provided as-is under the MIT License. The authors accept no liability for misuse or deployment in production systems.