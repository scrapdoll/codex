# codex-arg0

Dispatch logic that inspects `argv[0]` and command-line arguments to
redirect execution to helper binaries such as `codex-linux-sandbox` or the
`apply_patch` tool. It also loads environment variables from `.env` files
and runs the supplied async entry point on a Tokio runtime.

## Interface

```rust
pub fn arg0_dispatch_or_else<F, Fut>(main_fn: F) -> anyhow::Result<()>
where
    F: FnOnce(Option<PathBuf>) -> Fut,
    Fut: Future<Output = anyhow::Result<()>>;
```
