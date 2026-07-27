# provemark

Tooling for **content provenance & authenticity** — verifiable
[C2PA](https://c2pa.org) Content Credentials for the PHP ecosystem, including
machine-readable marking of AI-generated content under the **EU AI Act,
Article 50**.

## Projects

### [content-credentials](https://github.com/provemark/content-credentials)

A PHP library to build, sign, read and verify C2PA manifests — a
framework-agnostic Core plus an optional Laravel integration. The private
signing key stays isolated from your web application, not baked into it.

```bash
composer require provemark/content-credentials
```
