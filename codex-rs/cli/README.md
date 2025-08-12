# codex-cli

Defines the top-level `codex` command and supporting subcommands.
The crate hosts argument parsing, sandbox helpers and other
utilities used by the CLI entry points.

## Interface

```rust
#[derive(Debug, Parser)]
pub struct SeatbeltCommand {
    pub full_auto: bool,
    pub config_overrides: CliConfigOverrides,
    pub command: Vec<String>,
}

#[derive(Debug, Parser)]
pub struct LandlockCommand {
    pub full_auto: bool,
    pub config_overrides: CliConfigOverrides,
    pub command: Vec<String>,
}
```
