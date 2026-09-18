# nix

**The AI Layer for your codebase.**

> Give your coding agent context. Not another agent.

Nix is a local-first AI infrastructure layer for software and intelligent agents.

It gives AI coding agents deep, structured, searchable understanding of your codebase — including files, symbols, dependencies, architecture, Git history, project memory, and related context — while keeping your source code on your machine.

**NixAI** is the npm package name. `nix` is the installed CLI command.

---

## Why Nix?

Modern AI coding agents are powerful, but their understanding of a codebase is often limited to the files and context currently available to them.

Nix builds a persistent context layer around your project.

```text
Your Codebase
      │
      ▼
┌─────────────────────┐
│        Nix          │
│                     │
│  Indexing           │
│  Code Intelligence  │
│  Semantic Search    │
│  Git Intelligence   │
│  Project Memory     │
│  Architecture       │
│  Verification       │
└──────────┬──────────┘
           │
           ▼
      MCP Interface
           │
           ▼
   AI Coding Agents
```

Nix is designed around a simple idea:

> **Don't make the developer explain the codebase.  
> Don't make the agent rediscover the codebase.**

---

## Features

| Category | Capabilities |
|---|---|
| **Search** | Hybrid lexical + semantic search, BM25, embeddings, symbol search |
| **Code Intelligence** | Tree-sitter parsing, symbols, call graphs, dependency graphs |
| **Context** | Related files, architecture graphs, comprehensive context packages |
| **Git** | History, blame, changes, hotspots, affected files |
| **Memory** | Persistent project memories and agent handoffs |
| **Security** | Secret scanning, malicious-code detection, index recovery |
| **Verification** | Sandboxed test/build execution and repair workflows |
| **MCP** | 12 tools for AI agents through stdio transport |
| **Embeddings** | Local Transformers.js, Ollama, LM Studio, OpenAI-compatible and custom HTTP providers |

### Supported languages

TypeScript · JavaScript · Python · Go · Rust · Java · C · C++ · C# · PHP · Ruby

---

## Installation

### npm

```bash
npm install -g nixai
```

Verify the installation:

```bash
nix --version
nix --help
```

> **Note:** `nixai` is the npm package name and `nix` is the CLI command.

---

## Quick Start

Install Nix:

```bash
npm install -g nixai
```

Configure your AI coding agents:

```bash
nix setup
```

Initialize Nix inside your project:

```bash
cd your-project
nix init
nix index
```

That's it.

Your AI coding agent can now access your project's context through MCP.

### Automatic agent setup

`nix setup` can:

1. Detect your operating system
2. Verify the Nix installation
3. Detect supported AI coding agents
4. Offer to configure them automatically
5. Report what was configured

Supported agents include:

- OpenCode
- Claude Code
- Cursor
- Cline
- Continue
- Windsurf

---

## CLI

### Setup & Diagnostics

| Command | Description |
|---|---|
| `nix setup` | Configure Nix MCP for supported coding agents |
| `nix setup --remove` | Remove Nix MCP configuration |
| `nix setup --agents opencode,cursor` | Configure specific agents |
| `nix setup --yes` | Non-interactive setup |
| `nix doctor` | Run system diagnostics |
| `nix doctor --json` | Output machine-readable diagnostics |

### Project Management

| Command | Description |
|---|---|
| `nix init` | Initialize a Nix project |
| `nix index` | Incrementally index the project |
| `nix reindex` | Perform a full reindex |
| `nix status` | Show project status |
| `nix config` | View or modify configuration |
| `nix clean` | Clean index and cache |

### Search & Context

| Command | Description |
|---|---|
| `nix search <query>` | Search the codebase |
| `nix symbol <name>` | Find a symbol |
| `nix graph` | Show the architecture graph |
| `nix tree` | Show the project structure |
| `nix context <query>` | Generate a comprehensive context package |

### Git Intelligence

| Command | Description |
|---|---|
| `nix git status` | Show Git status |
| `nix git history` | Show commit history |
| `nix git changes` | Show recent changes |
| `nix git blame <file>` | Show Git blame |
| `nix git log <file>` | Show file history |

### Security & Verification

| Command | Description |
|---|---|
| `nix hardening scan` | Scan for secrets and malicious code |
| `nix hardening benchmark` | Run retrieval benchmarks |
| `nix hardening recover` | Recover a corrupted index |
| `nix verify affected` | Find files affected by Git changes |
| `nix verify test` | Run tests in a sandbox |
| `nix verify build` | Run builds in a sandbox |
| `nix verify repair` | Generate repair suggestions |

### MCP & Memory

| Command | Description |
|---|---|
| `nix mcp` | Start the MCP server |
| `nix memory add` | Add project memory |
| `nix memory list` | List memories |
| `nix memory search` | Search memories |
| `nix handoff` | Create or receive agent handoffs |

### Other

| Command | Description |
|---|---|
| `nix explain` | Explain selected code |
| `nix docs` | Manage documentation |
| `nix watch` | Watch for project changes |

---

## MCP

Nix exposes project intelligence through the Model Context Protocol (MCP).

After running:

```bash
nix setup
```

your supported AI coding agent can access Nix automatically.

### MCP tools

| Tool | Description |
|---|---|
| `search_code` | Lexical + semantic code search |
| `search_symbols` | Search symbols by name or kind |
| `get_file` | Read file contents |
| `get_symbol` | Get symbol details |
| `find_references` | Find symbol references |
| `find_callers` | Find function callers |
| `find_dependencies` | Find dependencies |
| `get_related_context` | Generate comprehensive context |
| `get_project_memory` | Retrieve project memories |
| `get_architecture` | Get the architecture graph |
| `get_git_context` | Retrieve Git history and changes |
| `get_project_structure` | Get the project directory tree |

---

## Configuration

Nix stores project configuration in:

```text
.nix/config.json
```

Example:

```json
{
  "version": 1,
  "project": {
    "name": "my-project",
    "root": "."
  },
  "index": {
    "ignoredPaths": [],
    "maxFileSize": 1048576
  },
  "search": {
    "weights": {
      "lexicalWeight": 1,
      "semanticWeight": 1,
      "symbolWeight": 1,
      "pathWeight": 1,
      "graphWeight": 1,
      "recencyWeight": 1
    }
  },
  "embeddings": {
    "provider": "local",
    "model": "Xenova/all-MiniLM-L6-v2",
    "apiBase": "",
    "apiKey": "",
    "dimensions": 384,
    "batchSize": 32
  },
  "mcp": {
    "enabled": true
  },
  "hardening": {
    "enableSecretScanning": true,
    "enableMaliciousDetection": true,
    "enableCorruptedIndexRecovery": true,
    "maxFileSizeForScanning": 1048576
  }
}
```

---

## Embedding Providers

Nix supports multiple embedding backends:

| Provider | Configuration | Description |
|---|---|---|
| `local` | Default | Runs locally through Transformers.js |
| `ollama` | `apiBase` | Local Ollama server |
| `lmstudio` | `apiBase` | Local LM Studio server |
| `openai` | `apiKey`, `apiBase` | OpenAI-compatible API |
| `custom` | Custom configuration | HTTP embedding endpoint |

The default local provider does not require an API key.

---

## Architecture

```text
┌──────────────────────────────────────────────────────────┐
│                         Nix Core                          │
├──────────────────────────────────────────────────────────┤
│ Indexer │ Search │ Storage │ Memory │ Git │ Verification │
└──────┬────────┬──────────┬─────────┬─────┬───────────────┘
       │        │          │         │
       ▼        ▼          ▼         ▼
   ┌───────┐ ┌────────┐ ┌────────┐ ┌────────┐
   │  CLI  │ │ SQLite │ │  MCP   │ │ Memory │
   └───────┘ └────────┘ └────────┘ └────────┘
```

---

## Privacy

Nix is designed to keep project intelligence local.

- **No telemetry by default**
- **No cloud service required**
- **No source-code upload**
- **Completely offline capable**
- Project indexes and context remain on your machine

External embedding providers can be configured when explicitly desired.

---

## Development

Clone the repository and install dependencies:

```bash
pnpm install
```

Build:

```bash
pnpm build
```

Run linting:

```bash
pnpm lint
```

Run tests:

```bash
pnpm test
```

Typecheck:

```bash
pnpm typecheck
```

Format:

```bash
pnpm format
```

---

## Requirements

- Node.js `>= 20.0.0`
- pnpm `>= 9.0.0` for development

---

## Uninstall

Remove the global npm package:

```bash
npm uninstall -g nixai
```

Remove Nix project data:

```bash
rm -rf .nix
```

Remove Nix MCP configuration:

```bash
nix setup --remove
```

---

## Security

If you discover a security vulnerability, please follow the security policy in:

```text
SECURITY.md
```

Do not publicly disclose sensitive vulnerabilities before they have been responsibly reported.

---

## Contributing

Contributions, bug reports, ideas, and improvements are welcome.

See:

```text
CONTRIBUTING.md
```

---

## License

MIT — see [`LICENSE`](./LICENSE).

---

<p align="center">
  <strong>nix</strong>
  <br />
  Context intelligence for AI coding agents.
</p>
