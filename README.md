# Semantic Scholar MCP server

Made with [FastMCP](https://github.com/jlowin/fastmcp), forked from [benhaotang/mcp-semantic-scholar-server](https://github.com/benhaotang/mcp-semantic-scholar-server) to use `uv` to manage dependencies.

## Installation

1. Install [`uv`](https://docs.astral.sh/uv/getting-started/installation/) and [`fastmcp`](https://github.com/jlowin/fastmcp?tab=readme-ov-file#installation) (you can run `uv pip install fastmcp --system` to install it system wide)
2. Clone this repo
3. Run `uv sync` to install dependencies

### Automatic

1. Run `fastmcp install semantic-scholar-plugin.py` to install to Claude
2. Done!

### Manual

1. Open your Claude config file (in macOS, it's at `~/Library/Application Support/Claude/claude_desktop_config.json`)
2. Get the directory of where you cloned this repo by running `pwd` in the terminal
3. Add the following to the `globalShortcut` object:

```json
"semantic-scholar": {
      "command": "uv",
      "args": [
        "run",
        "--with",
        "fastmcp",
        "fastmcp",
        "run",
        "\path\to\this\cloned\repo\semantic-scholar-plugin.py"
      ]
    }
```

## Troubleshooting

### `Error: spawn uv ENOENT`

Claude can't find `uv`. Make sure you have it installed and run `which uv` to get the path (e.g. `/Users/username/.local/bin/uv`).

Then update your Claude config to use that path:

```diff
 "Semantic Scholar Search": {
-      "command": "uv",
+      "command": "/Users/username/.local/bin/uv",
      "args": [
        "run",
```

### `INFO Processing request of type __init__.py:431 ListToolsRequest`

If you see `INFO Processing request of type __init__.py:431 ListToolsRequest` in Cline, you can ignore them as this will not affect it from working, this is due to current incomplete implementation of the function description and listing support.
