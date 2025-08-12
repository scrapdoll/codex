# codex-ollama

Helpers for running Codex with open-source models via a local
[Ollama](https://ollama.ai) server. The crate checks that the
server is reachable, downloads models when needed and exposes
progress reporters for the pull process.

## Interface

```rust
pub use client::OllamaClient;
pub use pull::{CliProgressReporter, PullEvent, PullProgressReporter, TuiProgressReporter};

pub const DEFAULT_OSS_MODEL: &str = "gpt-oss:20b";

pub async fn ensure_oss_ready(config: &Config) -> std::io::Result<()>;
```
