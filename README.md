# Zomato-mcp-server-claude
Connecting a mcp-server of zomato to claude desktop by editing the developer's config file and testing it to order food from zomato by typing in claude.
Connect Claude Desktop to a Remote MCP Server
This guide provides step-by-step instructions on how to connect your Claude Desktop application to an external Model Context Protocol (MCP) server.

This integration allows Claude to act as an "agent," giving it the ability to interact with real-world services (like ordering food, checking code repositories, or querying databases) directly from your chat interface.

Prerequisites
Before you begin, ensure you have the following installed:

Claude Desktop App: This guide is specifically for the official desktop application (macOS or Windows).

Node.js: The zomato-mcp configuration (and many others) uses npx (Node Package Executor) to run the remote connection script. You must have Node.js and npm installed.

🚀 Configuration Steps
Step 1: Locate Your Claude Config File
First, you need to find and open the claude_desktop_config.json file. This file may not exist until you open the "Developer" settings in the app, or you may need to create it.

Step 2: Edit the Configuration File
Open the claude_desktop_config.json file in a text editor (like VS Code, Notepad, or TextEdit).
You need to add an mcpServers object.
If your file is empty or doesn't exist: Copy and paste the entire block below.
If your file already has content: Carefully add the mcpServers key. If it already has an mcpServers object, just add the "zomato-mcp": { ... } entry inside it.

{
  "mcpServers": {
    "zomato-mcp": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp-server.zomato.com/mcp"
      ]
    }
  }
}


Step 3: Restart Claude
This is a critical step. The Claude Desktop app only reads this configuration file on startup.
Completely quit the application. (On macOS, Cmd + Q or right-click the dock icon and "Quit").
Re-open the Claude Desktop app.

Step 4: Authenticate (First-Time Use)
The server is now connected, but it doesn't know who you are on Zomato. The first time you try to use it, Claude will ask for authentication.
