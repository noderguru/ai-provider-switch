# 🚀 ai-provider-switch

<p align="center">
  <b>Interactive provider switcher for Claude Code</b><br/>
  Switch between Ollama Cloud, Claude, GLM (z.ai), and DeepSeek from one menu.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/bash-script-121011?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash">
  <img src="https://img.shields.io/badge/Claude_Code-supported-7c3aed?style=for-the-badge" alt="Claude Code">
  <img src="https://img.shields.io/badge/fzf-powered-0f172a?style=for-the-badge" alt="fzf">
  <img src="https://img.shields.io/badge/license-MIT-16a34a?style=for-the-badge" alt="MIT">
</p>

---

## Table of contents

- [Why this exists](#why-this-exists)
- [Features](#features)
- [Supported providers](#supported-providers)
- [Installation](#installation)
- [Usage](#usage)
- [Key storage](#key-storage)
- [Manage saved keys](#manage-saved-keys)
- [tmux workflow](#tmux-workflow)
- [Requirements](#requirements)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## Why this exists

If you use **Claude Code** with multiple backends, switching providers manually gets annoying fast.

`ai-switch` gives you one interactive command that:

- checks dependencies,
- lets you choose a provider,
- lets you choose a model,
- loads the right API settings,
- starts Claude Code with the selected backend.

It is especially useful if you regularly move between:

- free and paid Ollama Cloud models,
- direct Anthropic Claude models,
- GLM via z.ai,
- DeepSeek API,
- separate `tmux` sessions or multiple projects.

---

## Features

- ⚡ One command to switch AI backends for Claude Code
- 🧭 Interactive `fzf` menus
- 🔐 Built-in **Manage saved keys** menu
- 💾 Saves provider keys to one persistent config file
- 🛠 Auto-checks required tools
- 📦 Auto-installs itself to `/usr/local/bin/ai-switch`
- 🧵 Great fit for `tmux` workflows
- 🧩 Separate key storage for each provider

---

## Supported providers

### Ollama Cloud (Free)

Available models include:

- `minimax-m2.7:cloud`
- `minimax-m2.5:cloud`
- `glm-4.7:cloud`
- `glm-4.6:cloud`
- `qwen3.5:cloud`
- `qwen3-coder:480b-cloud`
- `deepseek-v3.1:671b-cloud`
- `deepseek-v3.2:cloud`
- `gpt-oss:120b-cloud`
- `ministral-3:14b-cloud`
- `mistral-large-3:675b-cloud`
- `nemotron-3-super`
- `gemini-3-flash-preview`

Uses:

- `OLLAMA_API_KEY`

### Ollama Cloud (Paid Pro/Max)

Available models include:

- `deepseek-v4-flash:cloud`
- `deepseek-v4-pro:cloud`
- `kimi-k2.6:cloud`
- `glm-5.1:cloud`
- `glm-5:cloud`

Uses:

- `OLLAMA_API_KEY`

### Claude

Available models:

- `claude-opus-4-7`
- `claude-sonnet-4-6`
- `claude-haiku-4-5-20251001`

Uses:

- `ANTHROPIC_API_KEY`

### GLM (z.ai)

Available models:

- `glm-5.1`
- `glm-5`
- `glm-5-turbo`

Uses:

- `ZAI_API_KEY`

### DeepSeek API (Pay-per-token)

Available models:

- `deepseek-v4-pro`
- `deepseek-v4-flash`

Uses:

- `DEEPSEEK_API_KEY`

---

## Installation

### Quick install

```bash
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o /tmp/ai-switch && chmod +x /tmp/ai-switch && sudo mv /tmp/ai-switch /usr/local/bin/ai-switch
```

Then run:

```bash
ai-switch
```

### Manual install

```bash
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o ai-switch
chmod +x ai-switch
sudo cp ai-switch /usr/local/bin/ai-switch
rm -f ai-switch
hash -r
```


> [!TIP]
> You can also run the script directly once with `bash ./ai-switch`.  
> The script is designed to live as a global command at `/usr/local/bin/ai-switch`.

---

## Usage

Start the menu:

```bash
ai-switch
```

<img width="448" height="411" alt="image" src="https://github.com/user-attachments/assets/4b91e670-9784-449f-8935-879d49a79b82" />

<img width="803" height="382" alt="image" src="https://github.com/user-attachments/assets/d534d286-daaf-4d20-bc0a-38ba81648f6c" />

> [!NOTE]
> If a provider key is already saved, the script reuses it automatically.  
> If not, it shows the correct link and waits for key input.

---

## Key storage

All provider keys are stored in one persistent file:

```bash
$HOME/.env_ai-provider-switch
```

Example:

```bash
OLLAMA_API_KEY="..."
ANTHROPIC_API_KEY="..."
ZAI_API_KEY="..."
DEEPSEEK_API_KEY="..."
```

This means:

- Ollama key does **not** overwrite DeepSeek key
- Claude key does **not** overwrite z.ai key
- all providers can coexist in one config file

> [!IMPORTANT]
> The script stores keys per provider, not per project directory.

---

## Manage saved keys

`ai-switch` includes a built-in key manager.

You can:

- Show saved keys
- Update Ollama key
- Update Claude key
- Update GLM (z.ai) key
- Update DeepSeek key
- Delete one key
- Delete all keys
- Go back to the main menu

Saved values are shown in masked form for safety.

---

## tmux workflow

This tool works very well with `tmux`.

Example:

```bash
# Session 1
tmux new -s frontend
cd ~/frontend-project
ai-switch

# Session 2
tmux new -s backend
cd ~/backend-project
ai-switch

# Session 3
tmux new -s experiments
cd ~/llm-tests
ai-switch
```

This makes it easy to use different providers for different tasks.

---

## Requirements

| Tool | Purpose |
|------|---------|
| Node.js | Required by Claude Code tooling |
| Ollama | Required for Ollama provider flow |
| Claude Code | Main CLI runner |
| fzf | Interactive menu interface |

The script checks these automatically at startup.

---

## Troubleshooting

### `ai-switch: command not found`

Reinstall the command to `/usr/local/bin`:

```bash
sudo cp ai-switch /usr/local/bin/ai-switch
chmod +x /usr/local/bin/ai-switch
hash -r
```

### Claude native install is not found

Add Claude native path:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### Claude warns about multiple installations

```bash
rm -f /usr/local/bin/claude
hash -r
which -a claude
claude doctor
```

### Saved keys seem missing

Check whether this file exists:

```bash
ls -l $HOME/.env_ai-provider-switch
```

---

## License

MIT

Built by [noderguru](https://github.com/noderguru)
