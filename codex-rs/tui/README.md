# codex-tui

Interactive terminal user interface for Codex. It presents multiple
panes, history navigation and approval prompts using the
[`ratatui`](https://docs.rs/ratatui) toolkit.

## Interface

```rust
pub use cli::Cli;

pub async fn run_main(
    cli: Cli,
    codex_linux_sandbox_exe: Option<PathBuf>,
) -> std::io::Result<codex_core::protocol::TokenUsage>;
```
