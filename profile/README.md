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

### [stateful-check](https://github.com/provemark/stateful-check)

Model-based (stateful) property testing for PHP: generate sequences of commands, check
them against a shadow model, and shrink a failure to a minimal counterexample. Also a
stateless property runner and opt-in edge-biased generation. No runtime dependencies.
