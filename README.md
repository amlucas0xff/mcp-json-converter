# MCP JSON Converter 🖥️

> **Linux Terminal-Style MCP Server Configuration Converter**

A single-page web application that converts MCP (Model Context Protocol) server JSON configurations into Claude Code CLI commands with an authentic Linux terminal interface.

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-green)](https://your-username.github.io/mcp-json-converter)
[![HTML5](https://img.shields.io/badge/HTML5-Valid-orange)](https://validator.w3.org/)
[![Mobile Responsive](https://img.shields.io/badge/Mobile-Responsive-blue)](https://your-username.github.io/mcp-json-converter)

## ✨ Features

- 🖥️ **Authentic Linux Terminal UI** - Complete with terminal colors, cursor animations, and command prompts
- 🔄 **Multi-Format Support** - Handles `mcpServers` objects, single configurations, and plain JSON objects
- 📱 **Mobile Responsive** - Optimized for desktop, tablet, and mobile devices
- ⚡ **Real-time Conversion** - Instant JSON-to-CLI command generation
- 📋 **Smart Clipboard** - HTTPS-compatible clipboard operations with fallback support
- 🎯 **Single-File Architecture** - Zero dependencies, perfect for GitHub Pages
- 🔧 **SOLID Principles** - Clean, maintainable code following software engineering best practices

## 🚀 Quick Start

### Online Usage (Recommended)

1. Visit the live demo: [https://your-username.github.io/mcp-json-converter](https://your-username.github.io/mcp-json-converter)
2. Paste your MCP JSON configuration into the terminal input
3. Click "convert-to-commands" or press `Ctrl+Enter`
4. Copy generated Claude Code CLI commands

### Local Usage

1. Download `index.html` from this repository
2. Open the file in any modern web browser
3. Start converting your MCP configurations!

## 📖 Usage Guide

### Input Formats Supported

#### 1. MCP Servers Object
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

#### 2. Single Server Configuration
```json
{
  "command": "npx", 
  "args": ["-y", "@modelcontextprotocol/server-github"],
  "env": {
    "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_PERSONAL_ACCESS_TOKEN}"
  }
}
```

#### 3. Plain Object (Auto-detected)
```json
{
  "filesystem": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/directory"]
  }
}
```

### Output Example

For the brave-search example above, the tool generates:

```bash
claude mcp add brave-search -s user -e BRAVE_API_KEY="your_api_key_here" -- npx -y @modelcontextprotocol/server-brave-search
```

### Keyboard Shortcuts

- `Ctrl+Enter` (Windows/Linux) or `Cmd+Enter` (Mac): Convert JSON
- `Ctrl+L` (Windows/Linux) or `Cmd+L` (Mac): Clear input

## 🏗️ Architecture

This project follows **SOLID principles** and **KISS (Keep It Simple, Stupid)** methodology:

### Single Responsibility Functions
- **Parsing**: `parseJsonInput()`, `detectJsonFormat()`, `parseMcpServers()`
- **Validation**: `validateMcpConfig()`, `validateServerName()`, `validateEnvironmentVars()`
- **Command Building**: `buildBaseCommand()`, `addEnvironmentVariables()`, `addCommandSeparator()`
- **UI Rendering**: `renderSingleServerCommands()`, `renderMultiServerSelection()`
- **Error Handling**: `handleParsingError()`, `handleValidationError()`, `handleConversionError()`
- **Coordination**: `convertJsonToCommands()`, `coordinateConversion()`, `handleSingleServer()`

### File Structure
```
mcp-json-converter/
├── index.html              # Main application (50KB, optimized)
├── 404.html               # GitHub Pages SPA routing support
├── robots.txt             # SEO crawler instructions
├── sitemap.txt            # Search engine sitemap
├── README.md              # This documentation
├── ARCHITECTURE_ANALYSIS.md # Technical analysis
├── shrimp-rules.md        # Development guidelines
├── LICENSE                # MIT License
└── logs/                  # Claude Code session logs (do not modify)
```

## 🌐 GitHub Pages Deployment

### For Repository Owners

1. **Create GitHub Repository**:
   ```bash
   git init
   git add index.html 404.html robots.txt sitemap.txt README.md LICENSE
   git commit -m "Initial commit: MCP JSON Converter with SPA support"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/mcp-json-converter.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**:
   - Go to repository **Settings** → **Pages**
   - Select **Source**: Deploy from a branch
   - Select **Branch**: `main` → `/ (root)`
   - Click **Save**

3. **Access Your Tool**:
   - Your tool will be live at: `https://YOUR-USERNAME.github.io/mcp-json-converter`
   - Updates are automatic when you push to main branch

### For Forkers

1. **Fork this repository** using GitHub's fork button
2. **Enable GitHub Pages** in your fork's settings (as above)
3. **Customize** the tool if needed
4. **Your fork** will be available at: `https://YOUR-USERNAME.github.io/mcp-json-converter`

## 🔧 Browser Compatibility

- ✅ **Chrome/Edge** 90+ (full support)
- ✅ **Firefox** 88+ (full support) 
- ✅ **Safari** 14+ (full support)
- ⚠️ **IE** - Not supported (modern ES6+ features required)

### HTTPS Requirements
- **Clipboard API** requires HTTPS (automatically provided by GitHub Pages)
- **Fallback mechanism** available for older browsers

### SPA GitHub Pages Features
- ✅ **404.html redirect** - Handles direct URL routing
- ✅ **SEO optimization** - robots.txt and sitemap.txt included  
- ✅ **Single-page routing** - Future-ready for multi-route expansion

## 🛠️ Development

### Local Development
```bash
# Serve locally for testing
python3 -m http.server 8000
# or
npx serve .

# Access at http://localhost:8000
```

### Code Quality Guidelines
- Functions limited to **20 lines max** (KISS principle)
- **Single Responsibility** - each function does one thing well
- **No external dependencies** - pure HTML/CSS/JS
- **Mobile-first responsive** design

## 🐛 Troubleshooting

### Common Issues

**"Clipboard access denied"**
- Ensure you're using HTTPS (required for clipboard API)
- GitHub Pages automatically provides HTTPS

**"JSON parsing error"**
- Validate your JSON using [jsonlint.com](https://jsonlint.com)
- Ensure proper escaping of quotes and special characters

**"No commands generated"**
- Check that your JSON contains `command` and `args` fields
- Verify the structure matches one of the supported formats

**Mobile display issues**
- The tool is optimized for mobile, but complex JSON may require horizontal scrolling
- Use landscape orientation for better experience

### Getting Help

1. **Check the browser console** (F12) for detailed error messages
2. **Validate your JSON** structure against the examples above
3. **Open an issue** in this repository with your JSON (remove sensitive data)

## 📊 Performance

- **File Size**: ~49KB (single file, optimized)
- **Load Time**: <500ms on 3G networks
- **Memory Usage**: <10MB RAM
- **Mobile Performance**: Optimized for low-end devices

## 🤝 Contributing

This project follows strict **SOLID/KISS principles**:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Follow** single-responsibility principle (max 20 lines per function)
4. **Test** on multiple browsers and devices
5. **Commit** with semantic messages: `git commit -m 'feat: add amazing feature'`
6. **Push** to branch: `git push origin feature/amazing-feature`
7. **Open** a Pull Request

### Development Rules
- ✅ **DO**: Extract small, focused functions
- ✅ **DO**: Add proper error handling
- ✅ **DO**: Test on mobile devices
- ❌ **DON'T**: Add external dependencies
- ❌ **DON'T**: Create functions >20 lines
- ❌ **DON'T**: Break single-file architecture

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Claude Code** - For the amazing MCP ecosystem
- **JetBrains Mono** - For the beautiful terminal font
- **GitHub Pages** - For free, reliable hosting
- **Model Context Protocol** - For standardizing AI tool interactions

---

**Built with ❤️ for the Claude Code community**

*Made possible by following SOLID principles and KISS methodology*