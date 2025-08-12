# codex-mcp-server

Prototype implementation of a Model Context Protocol server used in Codex.
It communicates over JSON-RPC on stdin/stdout, dispatches tool calls and
coordinates patch or execution approvals.

## Interface

```rust
pub use codex_tool_config::{
    CodexToolCallParam,
    CodexToolCallReplyParam,
};
pub use exec_approval::{
    ExecApprovalElicitRequestParams,
    ExecApprovalResponse,
};
pub use patch_approval::{
    PatchApprovalElicitRequestParams,
    PatchApprovalResponse,
};

pub async fn run_main(
    codex_linux_sandbox_exe: Option<PathBuf>,
) -> std::io::Result<()>;
```
