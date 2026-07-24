---
name: tavily-cli-installation
description: |
  Install the Tavily CLI and handle authentication errors.
---

# Tavily CLI Installation

## Quick Install

```bash
curl -fsSL https://cli.tavily.com/install.sh | bash
```

Or via Python package managers:

```bash
uv tool install tavily-cli
# or
pip install tavily-cli
```

## Verify Installation

Check if installed and authenticated in one command:

```bash
tvly --status
```

Output will show:

- Tavily CLI version
- Authentication status: `Authenticated via ...` or auth error

## Authentication

If not authenticated, run:

```bash
tvly login
```

The `tvly login` opens the browser for authentication automatically. This is the recommended method for agents.

If browser login is unavailable in your environment, set the API key directly:

```bash
export TAVILY_API_KEY="tvly-YOUR_KEY"
```

Or use the API key flag:

```bash
tvly --api-key tvly-YOUR_KEY search "your query"
```

Get an API key at [tavily.com](https://tavily.com).

If `TAVILY_API_KEY` is set in your environment, the plugin automatically passes it to shell commands.

## If You Fail to Authenticate

If ANY command returns an authentication error (e.g., "not authenticated", "unauthorized", "API key"), ask the user how they'd like to authenticate.

### Option 1: Browser Login (Recommended)

Run `tvly login` to automatically open the browser. Wait for them to confirm authentication, then retry the original command.

### Option 2: API Key

Ask for their API key, then run with:

```bash
export TAVILY_API_KEY="tvly-YOUR_KEY"
```

Tell them to add this export to their `~/.zshrc` or `~/.bashrc` for persistence, then retry the original command.

## Troubleshooting

### Command Not Found

If `tvly` command is not found after installation:

1. Make sure `~/.local/bin` is in PATH
2. Try: `npx tavily-cli --version`
3. Or reinstall: `curl -fsSL https://cli.tavily.com/install.sh | bash`

### Permission Errors

If you get permission errors during installation:

```bash
# Option 1: Fix PATH first
export PATH=~/.local/bin:$PATH

# Option 2: Reinstall correctly
curl -fsSL https://cli.tavily.com/install.sh | bash
```

### Rate Limits or Credit Issues

Check your account status:

```bash
tvly --status
```

If credits are exhausted, visit [tavily.com](https://tavily.com) to manage your account.
