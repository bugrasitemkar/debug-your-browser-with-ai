# How To Debug Your Browser with AI

*Photo by Timothy Dykes on Unsplash*

Now you don't need to copy and paste Console Logs to your favourite LLM. With the browser tools MCP, now your LLM is aware of your browser developer tools context.

The following step-by-step tutorial is for Cursor on Mac, but you can use any MCP supporting IDE.

## Requirements

* NodeJS is installed on your machine
* Google Chrome or a Chromium-based Browser
* MCP Client Application (Cursor, Windsurf, RooCode, Cline, Continue, Zed, Claude Desktop)

**Note:** Model Context Protocol (MCP) is specific to Anthropic models. When using an editor like Cursor, make sure to enable the composer agent with Claude 3.5 Sonnet selected as the model.

## 1 — Download the Browser Tools Chrome extension and install it

Alternatively, clone the repository and install the extension from the repository folder.

**Note:** You need to go to `chrome://extensions`, enable Dev Mode from the top right corner, and target the extension folder using the Load Unpacked button.

```
https://github.com/AgentDeskAI/browser-tools-mcp/releases/download/v1.2.0/BrowserTools-1.2.0-extension.zip
```

```bash
git clone https://github.com/AgentDeskAI/browser-tools-mcp.git
```

## 2 — Add MCP Server to Cursor

Go to Settings -> Tools & Integrations -> New MCP Server

```json
{
  "mcpServers": {
    "browser-tools": {
      "command": "npx",
      "args": ["-y", "@agentdeskai/browser-tools-mcp@1.2.0"]
    }
  }
}
```

## 3 — Run Terminal Command

```bash
npx @agentdeskai/browser-tools-server@1.2.0
```

**Note:** The terminal runs the command and starts to listen on localhost. Do not close this terminal instance.

## 4 — Open Console Dev Tools and go to the rightmost tab "BrowserToolsMCP"

* Enable Allow Auto-paste to Cursor
* Test Connection

Hopefully, the connection is successful and you see the "Connected to browser-tools-server v1.2.0 at localhost:3025" message.

## 5 — Test

Go to cursor chat and try a command such as "check console logs for warnings"

And you will see the tool calling and the response.

Read in medium format: https://hiddenlayerai.medium.com/how-to-debug-your-browser-with-ai-de1a883b5327
