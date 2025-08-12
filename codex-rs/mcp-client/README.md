# codex-mcp-client

Lightweight asynchronous client for the Model Context Protocol.
It spawns MCP servers as subprocesses, sends JSON-RPC requests and
pairs them with typed responses. A helper is provided for listing
tools exposed by servers.

## Interface

```rust
pub struct McpClient { /* fields omitted */ }

impl McpClient {
    pub async fn new_stdio_client(
        program: OsString,
        args: Vec<OsString>,
        env: Option<HashMap<String, String>>,
    ) -> std::io::Result<Self>;

    pub async fn send_request<R>(
        &self,
        params: R::Params,
        timeout: Option<Duration>,
    ) -> Result<R::Result>
    where
        R: ModelContextProtocolRequest,
        R::Params: Serialize,
        R::Result: DeserializeOwned;

    pub async fn send_notification<N>(&self, params: N::Params) -> Result<()>
    where
        N: ModelContextProtocolNotification,
        N::Params: Serialize;

    pub async fn initialize(
        &self,
        initialize_params: InitializeRequestParams,
        initialize_notification_params: Option<serde_json::Value>,
        timeout: Option<Duration>,
    ) -> Result<mcp_types::InitializeResult>;

    pub async fn list_tools(
        &self,
        params: Option<ListToolsRequestParams>,
        timeout: Option<Duration>,
    ) -> Result<ListToolsResult>;

    pub async fn call_tool(
        &self,
        name: String,
        arguments: Option<serde_json::Value>,
        timeout: Option<Duration>,
    ) -> Result<mcp_types::CallToolResult>;
}
```
