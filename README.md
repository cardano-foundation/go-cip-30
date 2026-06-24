# go-cip-30

`go-cip-30` verifies [CIP-30][cip30] data signatures so a Cardano wallet's
`api.signData()` result can be used for authentication and identification in a
Go backend.

The scope is intentionally narrow: validating CIP-30 data. It is not an HTTP
framework or middleware — you bring the transport, this library handles the
cryptography and the Cardano address logic.

## Install

```sh
go get github.com/cardano-foundation/go-cip-30
```

The package is imported as `cip30`.

## Quick start

A wallet returns a data signature as two hex-encoded CBOR strings. Verify the
signature and the message it was meant to sign:

```go
import cip30 "github.com/cardano-foundation/go-cip-30"

ds := cip30.DataSignature{Signature: sigHex, Key: keyHex}

result, err := cip30.Verify(ds, cip30.WithMessage([]byte("Sign in to Example")))
if err != nil {
    return err // unprocessable input: bad hex/CBOR, wrong lengths, etc.
}
if !result.Valid() {
    return errAuthFailed // signature did not verify, or a check failed
}

// result.KeyHash is the signer's stable identity (blake2b-224 of the key).
```

## Documentation

- [Project documentation](https://cardano-foundation.github.io/go-cip-30/) —
  usage guide and security considerations.
- [API reference](https://pkg.go.dev/github.com/cardano-foundation/go-cip-30) — full godoc
  with runnable examples.

Using a signature as an identity has sharp edges (self-asserted addresses,
stake-vs-payment matches, replay). Read the
[security guide](https://cardano-foundation.github.io/go-cip-30/security/) before going to
production.

## Development

[Moon](https://moonrepo.dev) is the task front door:

```sh
moon run root:format   # format
moon run root:lint     # lint
moon run root:build    # compile all packages
moon run root:test     # run tests
moon run root:check    # the full aggregate gate (also run in CI)
```

CI runs the same aggregate check:

```sh
moon ci --summary minimal
```

Prerequisites: Go 1.26.4 and Moon 2.x. The MkDocs documentation project under
`docs/` additionally needs Python 3.14+ and uv.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines, local setup
expectations, and the pull request workflow.

See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for the project code of conduct.

## Security

See [SECURITY.md](SECURITY.md) for the private vulnerability reporting path.

## License

Licensed under the [MIT License](LICENSE).

[cip30]: https://cips.cardano.org/cip/CIP-30
