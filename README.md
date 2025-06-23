# Cursor SWE flow

This repository showcases a simple set-up to enhance UX with cursor such that user can go from vibe-coding to software development with some structure. The goal is to take product requirements document (PRD) and technical design documents (TDD) and create a full set of GitHub issues in order to fully adhere to the specifications. Using agent mode and/or background agents one can then implement all of the issues one by one. The `.cursor/rules` includes useful directives that are always included in the request context, such that LLM behaves in a consistent manner and produces expected outputs.

## Credits

The work is inspired by https://github.com/snarktank/ai-dev-tasks

## Prerequisites

- This set-up assumes that you have functioning a GitHub MCP configured, as of writing this, the official cursor integration is not working for me. An alternative is adding your own by going to `Edit > Preferences > Cursor settings > Tools & integrations > MCP Tools > New MCP Server` 

```
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your-pat-token"
      }
    }
}
}
```

_Note: GitHub PAT can be configured under developer settings in GitHub. For best security practices use fine-grained tokens and apply principle of least privilege. Limit the scope to only the repositories you need access. For the approach describes here to fully work AI agent needs access to read repository contents (commits, branches...), read/write access to issues, read/write acces to pull requests, metadata (implicitly mandatory)_

## Usage

### Initial issue creation

Copy the contents of `instructions.md` file into a new AI chat in agent mode. Make sure to replace the parameters: your repo name, path to your PRD and TDD documents (for peace of mind explicitly set them to be in the message context)

### Individidual issue implementation

Simply open a new chat set it to agentic mode and prompt for "Implement issue #X in repo: username/repo" and watch the magic happen. The rules in `.cursor/rules/github-rules.mdc` instruct AI to implement the issue from start to finish and file a PR.