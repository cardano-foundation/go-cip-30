# Contributing

Thank you for your interest in contributing to `go-cip-30`.
Changes should keep the library focused on validating CIP-30 for authentication and identification.
For private vulnerability reporting, use [SECURITY.md](SECURITY.md) instead of public channels.

Please follow the [Code of Conduct](CODE_OF_CONDUCT.md) in all project interactions.

## Asking Questions

Use GitHub Discussions for questions and general discussion:
<https://github.com/cardano-foundation/go-cip-30/discussions>

## Reporting Bugs

Report non-security bugs through GitHub issues.
Include the following details when possible:

- version, commit, or environment details
- steps to reproduce
- expected behavior
- actual behavior
- logs, screenshots, or a minimal reproduction

If you are reporting a security issue, stop and follow [SECURITY.md](SECURITY.md) instead.

## Proposing Features

Open an issue before starting large or user-facing changes:
<https://github.com/cardano-foundation/go-cip-30/issues/new>

Describe the problem, the proposed behavior, and any compatibility impact.

## Pull Requests

Contributors should:

1. Keep changes focused and scoped to a single problem.
2. Add or update tests when behavior changes.
3. Update documentation when user-facing behavior changes.
4. Use Conventional Commit subjects, such as `feat: add config loader` or `fix: handle empty input`.
5. Make sure `moon run root:check` passes before requesting review.

## Local Setup

```sh
moon run root:check
```

Useful project commands:

```sh
moon run root:format
moon run root:lint
moon run root:build
moon run root:test
```

## Release Changes

Release Please reads Conventional Commit subjects to build changelogs and
release PRs. Use subjects such as `feat: add verifier option`,
`fix: reject malformed address`, or `docs: clarify replay guidance`.

Keep release-impacting commits clear; routine docs, CI, and maintenance commits
should use the appropriate non-release type.
