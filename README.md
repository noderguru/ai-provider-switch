# 🚀 ai-provider-switch

> One script to rule them all — switch between AI providers instantly ⚡

---

## 📖 English

### What It Does

`ai-switch` is a lightweight CLI tool that switches **Claude Code's AI backend** between:

- 🆓 **Free cloud models** via [Ollama](https://ollama.com/search) — run Llama, Qwen, Mistral and others locally or remotely without API fees
- 💳 **DeepSeek-V4** via [DeepSeek API](https://platform.deepseek.com) — powerful reasoning model with pay-per-use pricing

Perfect for toggling between free and paid providers depending on your task complexity.

✅ Checks dependencies (Node.js, Ollama, Claude Code)  
✅ Auto-detects installed providers  
✅ Switches active provider with one command  
✅ Validates versions and warns about conflicts  
✅ Great for **tmux sessions** — use different models per project window

### One-Line Install

```bash
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o ~/ai-switch && chmod +x ~/ai-switch && export PATH="$HOME:$PATH" && echo 'export PATH="$HOME:$PATH"' >> ~/.bashrc
```

Or manually:

```bash
# 1. Download
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o ~/ai-switch

# 2. Make executable
chmod +x ~/ai-switch

# 3. Add to PATH
export PATH="$HOME:$PATH"
echo 'export PATH="$HOME:$PATH"' >> ~/.bashrc
```

### Usage

```bash
ai-switch
```
<img width="428" height="330" alt="image" src="https://github.com/user-attachments/assets/5d381207-98e0-474a-a480-dc4eaf3530d9" />

<img width="557" height="358" alt="image" src="https://github.com/user-attachments/assets/843beba2-9e77-48ab-8610-1313d351bdf9" />


### Use With tmux

Run **different AI backends in each tmux window** — perfect for multi-project workflows:

```bash
!!!Example!!!
# Window 1 — frontend project with free Ollama model
tmux new -s progect_1
cd ~/my__project && ai-switch

# Window 2 — backend project with powerful DeepSeek-V4
tmux new -s progect_2
cd ~/my__project_2 && ai-switch
```

### Dependencies Checked

| Tool      | Purpose                          |
|-----------|----------------------------------|
| Node.js   | Runtime for JS-based tools       |
| Ollama    | Free cloud/local LLM runner      |
| Claude Code | Anthropic's CLI agent          |

---

## 📖 Русский

### Что делает скрипт

`ai-switch` — лёгкий CLI-инструмент для переключения **бэкенда Claude Code** между:

- 🆓 **Бесплатными облачными моделями** через [Ollama](https://ollama.com/search) — запускай Llama, Qwen, Mistral и другие локально или удалённо без платы за API
- 💳 **DeepSeek-V4** через [DeepSeek API](https://platform.deepseek.com) — мощная модель для рассуждений с оплатой по мере использования

Идеально для переключения между бесплатным и платным провайдерами в зависимости от сложности задачи.

✅ Проверяет зависимости (Node.js, Ollama, Claude Code)  
✅ Автоопределяет установленные провайдеры  
✅ Переключает активного провайдера одной командой  
✅ Проверяет версии и предупреждает о конфликтах  
✅ Удобно для **tmux-сессий** — разные модели для разных проектов

### Установка одной командой

```bash
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o ~/ai-switch && chmod +x ~/ai-switch && export PATH="$HOME:$PATH" && echo 'export PATH="$HOME:$PATH"' >> ~/.bashrc
```

Или вручную:

```bash
# 1. Скачать
curl -fsSL https://raw.githubusercontent.com/noderguru/ai-provider-switch/main/ai-switch -o ~/ai-switch

# 2. Сделать исполняемым
chmod +x ~/ai-switch

# 3. Добавить в PATH
export PATH="$HOME:$PATH"
echo 'export PATH="$HOME:$PATH"' >> ~/.bashrc
```

### Использование

```bash
ai-switch
```

### Почему удобно с tmux

Запускайте **разные AI-бэкенды в каждом окне tmux** — идеально для работы с несколькими проектами:

```bash
!!!Example!!!
# Window 1 — frontend project with free Ollama model
tmux new -s progect_1
cd ~/my__project && ai-switch

# Window 2 — backend project with powerful DeepSeek-V4
tmux new -s progect_2
cd ~/my__project_2 && ai-switch
```

### Проверяемые зависимости

| Инструмент | Назначение                      |
|------------|---------------------------------|
| Node.js    | Рантайм для JS-инструментов     |
| Ollama     | Бесплатный облачный/локальный запуск LLM |
| Claude Code| CLI-агент от Anthropic          |

---

## 🛠️ Troubleshooting

| Problem | Fix |
|---------|-----|
| `ai-switch: command not found` | `export PATH="$HOME:$PATH"` |
| Claude warns about multiple installs | `npm -g uninstall @anthropic-ai/claude-code` |
| Native Claude not in PATH | `echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc` |

---

## 📜 License

MIT — do whatever you want. Built with 💙 by [noderguru](https://github.com/noderguru).
