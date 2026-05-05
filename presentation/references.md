# Presentation References

## MCP Protocol

- [What is the Model Context Protocol (MCP)?](https://modelcontextprotocol.io/docs/getting-started/intro): official intro — MCP as a USB-C port for AI, how it connects agents to tools/resources/data, and broad ecosystem support (Claude, ChatGPT, Cursor, VS Code).
- [MCP Spec: Streamable HTTP Transport (2025-11-25)](https://modelcontextprotocol.io/specification/2025-11-25/basic/transports#streamable-http): the current remote transport spec — single MCP endpoint accepting POST (JSON-RPC call) and GET (SSE stream), session management via `MCP-Session-Id`, `MCP-Protocol-Version` header requirement, resumability via `Last-Event-ID`, and security requirements (Origin validation, auth).
- [MCP Spec: Tools (2025-11-25)](https://modelcontextprotocol.io/specification/2025-11-25/server/tools): tools are model-controlled; `tools/list` for discovery, `tools/call` for invocation; `inputSchema` / `outputSchema` as JSON Schema; two error levels (protocol errors vs. tool execution errors with `isError: true`); `listChanged` capability for dynamic tool updates.

## FastMCP Docs

- [Static Token Verification](https://gofastmcp.com/servers/auth/token-verification#static-token-verification): development and testing auth with predefined bearer tokens and claims.
- [StaticTokenVerifier SDK Reference](https://gofastmcp.com/python-sdk/fastmcp-server-auth-providers-jwt#statictokenverifier): maps static bearer token strings to client claims; for dev and testing only — never production.
- [Remote OAuth (RemoteAuthProvider)](https://gofastmcp.com/servers/auth/remote-oauth): integrates FastMCP with DCR-capable identity providers (WorkOS, Descope, modern OIDC); fully automated client registration flow.
- [OAuth Proxy (OAuthProxy)](https://gofastmcp.com/servers/auth/oauth-proxy): bridges MCP's DCR expectations to traditional OAuth providers that require pre-registered credentials (GitHub, Google, Azure, AWS, Discord).
- [Google OAuth Integration](https://gofastmcp.com/integrations/google): step-by-step guide for securing a FastMCP server with Google OAuth via the `OAuthProxy` / `GoogleProvider` pattern.
- [Server Configuration Reference](https://gofastmcp.com/servers/server?search=StaticTokenVerify#configuration-reference): `FastMCP` constructor options including auth, middleware, duplicate handling, and error masking.
- [Tool Error Handling](https://gofastmcp.com/servers/tools#error-handling): how tool exceptions are logged, converted to MCP errors, and masked with `mask_error_details`.
- [HTTP Deployment](https://gofastmcp.com/deployment/http): HTTP transport deployment, lifespan requirements, sessions, streaming, and scaling caveats.
- [FastMCP Horizontal Scaling](https://gofastmcp.com/deployment/http#horizontal-scaling): why `stateless_http=True` is required to disable session affinity when deploying behind a load balancer.
- [FastAPI Integration: Mounting an MCP Server](https://gofastmcp.com/integrations/fastapi#mounting-an-mcp-server): mounting FastMCP as an ASGI app and passing the MCP lifespan into FastAPI.
- [FastAPI Integration: Combining Lifespans](https://gofastmcp.com/integrations/fastapi#combining-lifespans): using `combine_lifespans` when FastAPI and FastMCP both need startup/shutdown handling.
- [FastAPI Integration: Web Frameworks](https://gofastmcp.com/integrations/fastapi#integration-with-web-frameworks): integration pattern for serving MCP alongside a web framework.
- [MCP Authorization Draft](https://modelcontextprotocol.io/specification/draft/basic/authorization): transport-level authorization, protected resource metadata discovery, authorization server metadata discovery, and OAuth requirements for HTTP transports.
- [Tool.from_function SDK Reference](https://gofastmcp.com/python-sdk/fastmcp-tools-base#from_function): converting plain Python callables into FastMCP `Tool` instances.
- [FastMCP.add_tool SDK Reference](https://gofastmcp.com/python-sdk/fastmcp-server-server#add_tool): registering `Tool` instances or tool callables with a FastMCP server.
- [Dependency Injection](https://gofastmcp.com/servers/dependency-injection#using-depends): `Depends`, current context helpers, custom dependencies, per-request caching, and schema exclusion for injected parameters.
- [FastMCP Lifespans](https://gofastmcp.com/servers/lifespan): server startup/shutdown and lifespan context access from tools.
- [FastMCP Tools](https://gofastmcp.com/servers/tools#tools): tool signatures, Pydantic input validation, structured output, output schemas, and error handling.
- [FastAPI Testing Dependencies](https://fastapi.tiangolo.com/advanced/testing-dependencies/#use-the-app-dependency-overrides-attribute): FastAPI's `app.dependency_overrides` test hook used as a contrast point for FastMCP.
- [svcs Overview](https://svcs.hynek.me/en/stable/): lightweight registry/container library for dependency inversion, service acquisition, cleanup, and testing.
- [svcs Core Concepts](https://svcs.hynek.me/en/stable/core-concepts.html): `Registry`, `Container`, `register_factory`, `register_value`, and async service acquisition via `aget()`.
- [svcs FastAPI Integration](https://svcs.hynek.me/en/stable/integrations/fastapi.html): lifespan integration, test-time registry replacement, and `register_value` testing pattern.
- [Pydantic Types](https://pydantic.dev/docs/validation/latest/concepts/types/): using built-in, standard library, constrained, and custom types for validation and serialization.
- [Pydantic Functional Validators](https://pydantic.dev/docs/validation/latest/api/functional_validators/#pydantic.functional_validators.AfterValidator): `AfterValidator` and other validator patterns for annotated types.
- [Pydantic Fields](https://pydantic.dev/docs/validation/latest/concepts/fields/): field metadata, constraints, descriptions, and annotated field declarations.
- [Pydantic Model Config](https://pydantic.dev/docs/validation/latest/concepts/config/): model-level configuration such as immutability, extra-field behavior, and validation settings.
- [Pydantic Extra Types: Country](https://pydantic.dev/docs/validation/latest/api/pydantic-extra-types/pydantic_extra_types_country/): ISO country code validation such as `CountryAlpha2`.
- [Pydantic Extra Types: Currency](https://docs.pydantic.dev/latest/api/pydantic_extra_types_currency_code/): ISO currency code validation such as `Currency` and `ISO4217`.
- [Pydantic Extra Types: Language](https://docs.pydantic.dev/latest/api/pydantic_extra_types_language_code/): language code validation such as `LanguageAlpha2`.
- [Pydantic Extra Types: Timezone Name](https://pydantic.dev/docs/validation/latest/api/pydantic-extra-types/pydantic_extra_types_timezone_name/): IANA timezone validation with `TimeZoneName`.

## MCP Tool Design Patterns
- [Autogenerating MCP Servers (Neon)](https://neon.com/blog/autogenerating-mcp-servers-openai-schemas)
- [MCP Tool Scalability Problem (Jenova)](https://www.jenova.ai/en/resources/mcp-tool-scalability-problem)
- [Build MCP Tools Like Ogres with Layers (Block)](https://engineering.block.xyz/blog/build-mcp-tools-like-ogres-with-layers)
- [Square MCP Server](https://github.com/square/square-mcp-server)
- [Blocks Playbook for Designing MCP Servers](https://engineering.block.xyz/blog/blocks-playbook-for-designing-mcp-servers)
- [MCP Tool Design Pattern (MCPBundles)](https://www.mcpbundles.com/blog/mcp-tool-design-pattern)
- [MCP Best Practices (Phil Schmid)](https://www.philschmid.de/mcp-best-practices)
- [MCP Server Design (Workato)](https://docs.workato.com/en/mcp/mcp-server-design.html)
- [Writing Tools for Agents (Anthropic)](https://www.anthropic.com/engineering/writing-tools-for-agents)
- [Tool Design (Speakeasy)](https://www.speakeasy.com/mcp/tool-design)
- [MCP Tool Strategy (AWS)](https://docs.aws.amazon.com/prescriptive-guidance/latest/mcp-strategies/mcp-tool-strategy.html)
- [MCP Tool Strategy Scope (AWS)](https://docs.aws.amazon.com/prescriptive-guidance/latest/mcp-strategies/mcp-tool-strategy-scope.html)
- [MCP Tool Strategy Definitions (AWS)](https://docs.aws.amazon.com/prescriptive-guidance/latest/mcp-strategies/mcp-tool-strategy-definitions.html)
- [MCP Tool Strategy Organization (AWS)](https://docs.aws.amazon.com/prescriptive-guidance/latest/mcp-strategies/mcp-tool-strategy-organization.html)
- [Pydantic Field Customizing JSON Schema](https://pydantic.dev/docs/validation/2.9/concepts/fields/#customizing-json-schema)
- [Pydantic Model-Level JSON Schema Customization](https://pydantic.dev/docs/validation/2.9/concepts/json_schema#model-level-customization)

## Tool Design Examples
- [Square MCP Server](https://github.com/square/square-mcp-server) — 3-tool pattern (`get_service_info`, `get_type_info`, `make_api_request`) covering all of Square's API; concrete example of phased tool exposure.

## Evaluation Strategy
- [Measuring what matters: How offline evaluation of GitHub MCP Server works](https://github.blog/ai-and-ml/generative-ai/measuring-what-matters-how-offline-evaluation-of-github-mcp-server-works/)
- [Demystifying evals for AI agents (Anthropic)](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)
- [How to test MCP servers effectively (Merge.dev)](https://www.merge.dev/blog/mcp-server-testing)
- [Writing Test Evals For Our MCP Server (Neon)](https://neon.com/blog/test-evals-for-mcp): real-world case study using Braintrust and LLM-as-a-judge; shows how improving tool descriptions alone moved pass rate from 60% to 100%. Covers stateful workflow evals, deterministic side-effect checks (`mainBranchIntegrityCheck`), and multi-trial runs for non-deterministic LLM outputs.
- [Evaluating MCP servers — a quick guide (MCPJam)](https://www.mcpjam.com/blog/mcp-evals): introduces "tool ergonomics" as a measurable discipline; defines the four classification metrics for MCP eval analysis — Accuracy, TPR/Recall (discoverability), FPR (over-triggering), and Precision (correct usage ratio). Also covers cross-model performance testing.
- [FastMCP Client Documentation (Pydantic)](https://pydantic.dev/docs/ai/mcp/fastmcp-client/)
- [Pydantic Evals Documentation](https://pydantic.dev/docs/ai/evals/evals/)