# OpenCode

## Config
Define globally in `~/.config/opencode/opencode.json`.

Key concepts:
 - For mcp auth, use env variables to avoid hardcoding secrets in the config file.
 - For [permissions](https://opencode.ai/docs/permissions/), last match wins.  So more specific rules should be listed after more general rules.

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "gpt-5.3-codex",
  "enabled_providers": ["github-copilot"],
  "plugin": [
    ""
  ],
  "mcp": {
    "Atlassian": {
      "type": "remote",
      "url": "https://mcp.atlassian.com/v1/mcp",
      "oauth": {}
    },
    "GitHub CXEPI": {
      "type": "remote",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer {env:GITHUB_CXEPI_PAT}"
      }
    }
  },
  "permission": {
    "*": "ask",
    "read": {
      "*": "ask",
      ".": "allow",
      "./*": "allow",
      "./**/*": "allow",
      "**/.env": "deny",
      "**/.env.*": "deny",
      "**/.ssh/config": "deny",
      "**/*.pem": "deny"
    },
    "edit": "ask",
    "glob": {
      "*": "ask",
      ".": "allow",
      "./*": "allow",
      "./**/*": "allow"
    },
    "grep": {
      "*": "ask",
      ".": "allow",
      "./*": "allow",
      "./**/*": "allow"
    },
    "bash": {
      "*": "ask",
      "make *": "allow",
      "pytest ./*": "allow",
      "wc ./*": "allow",
      "tail ./*": "allow",
      "tree ./*": "allow",
      "source ./*": "allow"
    },
    "task": "allow",
    "skill": "allow",
    "lsp": "allow",
    "question": "allow",
    "webfetch": "ask",
    "websearch": "ask",
    "external_directory": "ask",
    "doom_loop": "ask"
  }
}
```

## Tutorials
 - [The definitive guide to OpenCode](https://ai.sulat.com/the-definitive-guide-to-opencode-from-first-install-to-production-workflows-aae1e95855fb)
 - [Install GitHub MCP Server in OpenCode](https://github.com/github/github-mcp-server/blob/main/docs/installation-guides/install-opencode.md)
 - [How to add a GitHub MCP server to OpenCode](https://www.facebook.com/watch/?v=2017527445464799)