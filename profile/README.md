# provemark

PHP tooling for **verifiable trust** — from the provenance and authenticity of
content to the correctness of code.

## Projects

### [content-credentials](https://github.com/provemark/content-credentials)

A PHP library to build, sign, read and verify [C2PA](https://c2pa.org) manifests —
a framework-agnostic Core plus an optional Laravel integration, with machine-readable
marking of AI-generated content under the **EU AI Act, Article 50**. The private
signing key stays isolated from your web application, not baked into it.

```bash
composer require provemark/content-credentials
```

### [c2pa-verifier](https://github.com/provemark/c2pa-verifier)

A verifier for C2PA Content Credentials in **pure PHP**. It reads the manifest store
out of a JPEG, PNG, WebP or ISOBMFF file (MP4, MOV, AVIF, HEIC) and checks the claim
signature, the hash binding to the asset, the certificate chain against a trust list
you supply, the RFC 3161 timestamp and the revocation responses a signer staples into
its own signature — returning what `c2patool` returns: the same `validation_state` and
the same C2PA 2.4 §15 status codes.

For hosts that can run **no** second process, **no** native extension and **no**
binary — cheap shared hosting, where most WordPress and Drupal sites live. It does not
sign, holds no keys, and opens no network connection while verifying.

**A first version: thoroughly tested and never used.** Every fixture is measured
against `c2patool`, its answers compared with a second implementation in Go and a third
in Python, and 111 named obligations of the specification walked one by one — but
nobody has yet pointed it at their own files, their own trust list or their own
hosting. Treat a verdict as something to check, not as an answer.

```bash
composer require provemark/c2pa-verifier
```

### [c2pa-check](https://github.com/provemark/c2pa-check)

**Provemark C2PA Check**, a WordPress plugin that verifies the Content Credentials of
every JPEG, PNG and WebP uploaded to the Media Library with c2pa-verifier, and shows the
verdict in a Media Library column, a filter and the attachment details: *Verified:
trusted signer*, *Intact: signer not trusted*, *Does not verify*, *No Content
Credentials* or *Could not be checked* — and *AI-generated (signed)* only when a manifest
that verifies says so. The check runs in the background, so it never blocks or breaks an
upload; the plugin signs nothing and makes no network calls. It is c2pa-verifier's first
real user.

**Submitted to the WordPress.org plugin directory and awaiting review; not listed yet.**

### [stateful-check](https://github.com/provemark/stateful-check)

Model-based (stateful) property testing for PHP: generate sequences of commands, check
them against a shadow model, and shrink a failure to a minimal counterexample. Also a
stateless property runner and opt-in edge-biased generation. No runtime dependencies.
