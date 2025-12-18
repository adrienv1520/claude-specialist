# Features overview

Explore Claude's advanced features and capabilities.

---

## Core capabilities

These features enhance Claude's fundamental abilities for processing, analyzing, and generating content across various formats and use cases.

| Feature | Description | Availability |
|---------|-------------|--------------|
| [1M token context window](./developer-build-with-claude-context-windows.md#1m-token-context-window) | An extended context window that allows you to process much larger documents, maintain longer conversations, and work with more extensive codebases. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Agent Skills](./developer-agents-and-tools-agent-skills-overview.md) | Extend Claude's capabilities with Skills. Use pre-built Skills (PowerPoint, Excel, Word, PDF) or create custom Skills with instructions and scripts. Skills use progressive disclosure to efficiently manage context. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Batch processing](./developer-build-with-claude-batch-processing.md) | Process large volumes of requests asynchronously for cost savings. Send batches with a large number of queries per batch. Batch API calls costs 50% less than standard API calls. | <PlatformAvailability claudeApi bedrock vertexAi /> |
| [Citations](./developer-build-with-claude-citations.md) | Ground Claude's responses in source documents. With Citations, Claude can provide detailed references to the exact sentences and passages it uses to generate responses, leading to more verifiable, trustworthy outputs. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Context editing](./developer-build-with-claude-context-editing.md) | Automatically manage conversation context with configurable strategies. Supports clearing tool results when approaching token limits and managing thinking blocks in extended thinking conversations. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Effort](./developer-build-with-claude-effort.md) | Control how many tokens Claude uses when responding with the effort parameter, trading off between response thoroughness and token efficiency. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Extended thinking](./developer-build-with-claude-extended-thinking.md) | Enhanced reasoning capabilities for complex tasks, providing transparency into Claude's step-by-step thought process before delivering its final answer. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Files API](./developer-build-with-claude-files.md) | Upload and manage files to use with Claude without re-uploading content with each request. Supports PDFs, images, and text files. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [PDF support](./developer-build-with-claude-pdf-support.md) | Process and analyze text and visual content from PDF documents. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Prompt caching (5m)](./developer-build-with-claude-prompt-caching.md) | Provide Claude with more background knowledge and example outputs to reduce costs and latency. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Prompt caching (1hr)](./developer-build-with-claude-prompt-caching.md#1-hour-cache-duration) | Extended 1-hour cache duration for less frequently accessed but important context, complementing the standard 5-minute cache. | <PlatformAvailability claudeApi azureAi /> |
| [Search results](./developer-build-with-claude-search-results.md) | Enable natural citations for RAG applications by providing search results with proper source attribution. Achieve web search-quality citations for custom knowledge bases and tools. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Structured outputs](./developer-build-with-claude-structured-outputs.md) | Guarantee schema conformance with two approaches: JSON outputs for structured data responses, and strict tool use for validated tool inputs. Available on Sonnet 4.5, Opus 4.1, Opus 4.5, and Haiku 4.5. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Token counting](https://platform.claude.com/docs/en/api/messages-count-tokens.md) | Token counting enables you to determine the number of tokens in a message before sending it to Claude, helping you make informed decisions about your prompts and usage. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Tool use](./developer-agents-and-tools-tool-use-overview.md) | Enable Claude to interact with external tools and APIs to perform a wider variety of tasks. For a list of supported tools, see [the Tools table](#tools). | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |

## Tools

These features enable Claude to interact with external systems, execute code, and perform automated tasks through various tool interfaces.

| Feature | Description | Availability |
|---------|-------------|--------------|
| [Bash](./developer-agents-and-tools-tool-use-bash-tool.md) | Execute bash commands and scripts to interact with the system shell and perform command-line operations. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Code execution](./developer-agents-and-tools-tool-use-code-execution-tool.md) | Run Python code in a sandboxed environment for advanced data analysis. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Programmatic tool calling](./developer-agents-and-tools-tool-use-programmatic-tool-calling.md) | Enable Claude to call your tools programmatically from within code execution containers, reducing latency and token consumption for multi-tool workflows. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Computer use](./developer-agents-and-tools-tool-use-computer-use-tool.md) | Control computer interfaces by taking screenshots and issuing mouse and keyboard commands. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Fine-grained tool streaming](./developer-agents-and-tools-tool-use-fine-grained-tool-streaming.md) | Stream tool use parameters without buffering/JSON validation, reducing latency for receiving large parameters. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [MCP connector](./developer-agents-and-tools-mcp-connector.md) | Connect to remote [MCP](https://platform.claude.com/docs/en/mcp.md) servers directly from the Messages API without a separate MCP client. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Memory](./developer-agents-and-tools-tool-use-memory-tool.md) | Enable Claude to store and retrieve information across conversations. Build knowledge bases over time, maintain project context, and learn from past interactions. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Text editor](./developer-agents-and-tools-tool-use-text-editor-tool.md) | Create and edit text files with a built-in text editor interface for file manipulation tasks. | <PlatformAvailability claudeApi bedrock vertexAi azureAi /> |
| [Tool search](./developer-agents-and-tools-tool-use-tool-search-tool.md) | Scale to thousands of tools by dynamically discovering and loading tools on-demand using regex-based search, optimizing context usage and improving tool selection accuracy. | <PlatformAvailability claudeApiBeta bedrockBeta vertexAiBeta azureAiBeta /> |
| [Web fetch](./developer-agents-and-tools-tool-use-web-fetch-tool.md) | Retrieve full content from specified web pages and PDF documents for in-depth analysis. | <PlatformAvailability claudeApiBeta azureAiBeta /> |
| [Web search](./developer-agents-and-tools-tool-use-web-search-tool.md) | Augment Claude's comprehensive knowledge with current, real-world data from across the web. | <PlatformAvailability claudeApi vertexAi azureAi /> |