# codex-login

Handles authentication for Codex. It can read API keys from `auth.json`,
refresh ChatGPT tokens and provide access tokens to other crates.
The library also exposes helpers for logging in and out via the
`codex login` command.

## Interface

```rust
#[derive(Clone, Debug, PartialEq, Copy)]
pub enum AuthMode { ApiKey, ChatGPT }

#[derive(Debug, Clone)]
pub struct CodexAuth { /* fields omitted */ }

impl CodexAuth {
    pub fn from_api_key(api_key: &str) -> Self;
    pub fn from_codex_home(codex_home: &Path) -> std::io::Result<Option<CodexAuth>>;
    pub async fn get_token_data(&self) -> Result<TokenData, std::io::Error>;
    pub async fn get_token(&self) -> Result<String, std::io::Error>;
}

pub fn logout(codex_home: &Path) -> std::io::Result<bool>;
```
