---
title: "How to Connect GitHub MCP Server With Claude Desktop: A Step-by-Step Guide"
datePublished: Mon Apr 28 2025 13:44:30 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xqdkw000502lc3njs7tus
slug: how-to-connect-github-mcp-server-with-claude-desktop-a-step-by-step-guide-1b6bbd2c52b9
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608300629/e3b81b2d-7159-415d-bb9c-21a4f63e29c8.png

---

The integration of Claude Desktop with a GitHub MCP (Model Context Protocol) server unlocks powerful capabilities: you can automate repository management, analyze code, and interact with GitHub directly from your AI assistant. This guide will walk you through the entire process, from prerequisites to troubleshooting, ensuring a smooth connection between your GitHub MCP server and Claude Desktop.

### What is the GitHub MCP Server?

The GitHub MCP Server is a bridge that enables Claude Desktop (and other AI tools) to interact with your GitHub repositories via the Model Context Protocol. This allows for advanced automation, direct file access, and seamless workflow enhancements within your development environment.

### Prerequisites

Before you begin, make sure you have:

*   Claude Desktop installed (latest version recommended)
*   [Download — Claude](https://claude.ai/download)

*   Docker Desktop or Node.js and npm installed (depending on your preferred setup)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608291460/9445caf5-7624-4fef-8c6a-f2bc417409aa.png)

*   A GitHub account with a Personal Access Token (PAT) generated
*   Basic familiarity with editing configuration files

### Step 1: Generate a GitHub Personal Access Token

1.  Go to your [GitHub](https://github.com/Yash-Kavaiya) account settings.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608293007/44dcf6be-b7c2-4a10-bb83-6c7d8f0eac84.png)

1.  Navigate to Developer settings > Personal access tokens.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608294310/e3a0ad7d-87ea-4eb9-b100-38a7c4ad17d0.png)

1.  Click Generate new token.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608295949/2bf51785-b9a0-4dac-85bd-578f22df908b.png)

1.  Select the required scopes:

*   For full repository access: `repo`
*   Check all boxes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608297434/b624e16d-beea-421b-a016-d3ad09645710.png)

1.  Copy anyour token securely-you’ll need it for configuration.

### Step 2: Configure Claude Desktop to Use the GitHub MCP Server

You need to edit Claude Desktop’s configuration file to add the GitHub MCP server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608298984/4b17745f-7d28-4113-bb74-4cb238a74474.png)

Click on Edit Config File

### Locate the Configuration File

*   Windows:  
    `%APPDATA%/Claude/config.json`
*   macOS:  
    `~/Library/Application Support/Claude/claude_desktop_config.json`[5](https://allthings.how/how-to-set-up-github-mcp-server-for-use-with-claude-desktop-on-windows-and-mac/)

### Add the MCP Server Configuration

### For Docker Users:

Again, replace <YOUR\_TOKEN> with your GitHub PAT5.

### Step 4: Restart Claude Desktop

*   Completely close Claude Desktop (ensure it’s not running in the background).
*   Reopen Claude Desktop to load the new configuration[2](https://modelcontextprotocol.io/quickstart/user)[5](https://allthings.how/how-to-set-up-github-mcp-server-for-use-with-claude-desktop-on-windows-and-mac/).

### Step 5: Verify the Integration

*   Open Claude Desktop.
*   Look for a hammer icon in the bottom right corner of the input box-this indicates MCP servers are connected[2](https://modelcontextprotocol.io/quickstart/user)[3](https://www.eudaimoniatech.io/how-to-fix-claude-desktop-mcp-issues-on-windows-11-a-complete-guide/).
*   Start a new conversation and ask Claude to perform a GitHub operation, such as:
*   “List my repositories.”
*   “Create a new issue in my repo.”
*   If successful, Claude will interact with your GitHub repositories seamlessly[5](https://allthings.how/how-to-set-up-github-mcp-server-for-use-with-claude-desktop-on-windows-and-mac/).
*   Troubleshooting Tips
*   Permissions: On Windows, run Claude Desktop as administrator and ensure proper folder permissions for `%APPDATA%/Claude` and related directories[3](https://www.eudaimoniatech.io/how-to-fix-claude-desktop-mcp-issues-on-windows-11-a-complete-guide/).
*   Path Issues: Use absolute paths in your configuration and ensure environment variables are set correctly.
*   Logs: Check log files for errors:
*   macOS: `~/Library/Logs/Claude`
*   Windows: `%APPDATA%\Claude\logs` (look for `mcp.log` and `mcp-server-github.log`)
*   Docker Issues: Ensure Docker Desktop is running and accessible.
*   Node.js Issues: Ensure npm is installed globally and `npx` commands work without errors.

### Example Use Cases

*   Automate GitHub issue creation and management from your desktop.
*   Query and analyze code across your repositories using Claude’s natural language interface.
*   Manage pull requests, branches, and repository insights without leaving Claude Desktop

> With your GitHub MCP server connected, Claude Desktop becomes a powerful AI assistant for your development workflow-enabling real-time, context-aware GitHub operations right from your desktop.