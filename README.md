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

## Composition

Listed inside [`pj-presets:rust-cli`](https://github.com/yukimemi/pj-presets)
between `pj-base` and `pj-rust-cli`.

```sh
kata init github.com/yukimemi/pj-presets:rust-cli ./your-new-pj
```

## License

MIT.
