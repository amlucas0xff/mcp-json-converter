# MCP JSON Converter

Convert MCP (Model Context Protocol) server JSON configurations into Claude Code CLI commands.

## Features

- Terminal-style interface with authentic Linux appearance
- Supports multiple JSON formats: mcpServers objects, single configurations, and plain objects
- Mobile responsive design
- Real-time conversion with instant results
- Clipboard integration for easy copying
- Zero dependencies - single HTML file

## Usage

### Online
1. Visit the live demo
2. Paste your MCP JSON configuration
3. Press `Ctrl+Enter` to convert
4. Copy the generated commands

### Local
Download `index.html` and open in any modern browser.

## Supported Formats

### MCP Servers Object
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"]
    }
  }
}
```

### Single Server Configuration
```json
{
  "command": "npx", 
  "args": ["-y", "@modelcontextprotocol/server-github"]
}
```

### Plain Object
```json
{
  "filesystem": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-filesystem"]
  }
}
```

## Shortcuts

- `Ctrl+Enter`: Convert JSON
- `Ctrl+L`: Clear input

## Development

Single HTML file with modular JavaScript functions. No external dependencies.

## Deployment

### GitHub Pages
1. Push to GitHub repository
2. Enable Pages in Settings → Pages
3. Select main branch as source
4. Access at `https://username.github.io/repository-name`

## Requirements

Modern browser with ES6+ support. HTTPS required for clipboard functionality.

## Local Testing

```bash
python3 -m http.server 8000
```

## License

MIT License