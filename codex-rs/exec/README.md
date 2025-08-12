# codex-exec

Runs the Codex agent in response to user prompts.
The crate wires configuration, model selection and event
processing into a loop that streams Codex events to
human-friendly or JSON outputs.

## Interface

```rust
pub use cli::Cli;

pub async fn run_main(
    cli: Cli,
    codex_linux_sandbox_exe: Option<PathBuf>,
) -> anyhow::Result<()>;
```
