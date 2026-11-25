# pj-rust

Rust language layer for [kata](https://github.com/yukimemi/kata)
templates. Compose **above** [`pj-base`](https://github.com/yukimemi/pj-base)
and **below** [`pj-rust-cli`](https://github.com/yukimemi/pj-rust-cli).

## What this layer applies

| File | how | when |
|---|---|---|
| `Makefile.toml` | overwrite | always |
| `rust-toolchain.toml` | overwrite | always |
| `.github/workflows/ci.yml` | overwrite | always |

`always` means: re-applied on every `kata apply`. Edits you make to
these files locally will be reverted next sync — that's intentional;
these are the Rust-project house-keeping files that should track the
template, not drift per-PJ.

## Opt in to nextest for unit and integration tests

Set `PJ_RUST_TEST_RUNNER = "nextest-unit"` in the consumer's
Makefile.toml `[env]` and at the top level of `.kata/vars.toml`.
See [the Rust workflow guidance](AGENTS.md.rust) for CI profile
configuration and adoption requirements.

Examples and benches still run through `cargo test --examples --benches`.
Cargo's `--benches` can include lib and bin benchmark harnesses, so
their unit tests may run again even after nextest has run them.

Magi ignores the rendered `.github/workflows/ci.yml` and maintains
its own CI split. Do not overwrite its workflow using `kata apply`.
Adopt the local runner and synchronize its hand-maintained CI split
together in a separate change.

## Composition

Listed inside [`pj-presets:rust-cli`](https://github.com/yukimemi/pj-presets)
between `pj-base` and `pj-rust-cli`.

```sh
kata init github.com/yukimemi/pj-presets:rust-cli ./your-new-pj
```

## License

MIT.
