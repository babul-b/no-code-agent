# Your First No-Code Agent: Automating a Daily Task with n8n + Ollama

Standalone companion repo for the Medium article of the same name. This repo is self-contained — it doesn't depend on, or link to, any other article's repo.

📖 Medium article: *(link goes here once published)*

## What's in this repo

| File | What it is |
|---|---|
| [`article.md`](article.md) | The full article text (source of truth, also published to Medium) |
| [`article-for-medium.html`](article-for-medium.html) | Paste-ready version for Medium — see below |
| [`diagrams/architecture.png`](diagrams/architecture.png) | The architecture diagram used in the article |
| [`n8n-workflow/02-watch-and-summarize.json`](n8n-workflow/02-watch-and-summarize.json) | The exact workflow built in the article — import via n8n's **Menu → Import from File** |
| [`k8s/`](k8s/) | Placeholder — this article doesn't use Kubernetes yet, see [`k8s/README.md`](k8s/README.md) |

## Publishing to Medium

Medium does not accept plain Markdown — pasting a `.md` file shows literal `#` and `` ``` `` characters instead of formatting. Use `article-for-medium.html` instead:

1. Open `article-for-medium.html` in Chrome or Edge.
2. Press `Ctrl+A` to select everything, then `Ctrl+C` to copy.
3. In Medium, start a new story and press `Ctrl+V` to paste.

Headings, bold text, links, lists, blockquotes, and the diagram image should all come through correctly. Code blocks paste as plain monospace text — select each one afterward and click Medium's code-block icon (or press `Ctrl+Alt+6` / `Cmd+Option+6`) if you want Medium's code-block styling.

## Quick start (running the agent)

1. Have Ollama (`llama3.2:3b`), Docker Desktop, and n8n already installed (see the previous article, or [ollama.com](https://ollama.com) / [docker.com](https://www.docker.com/products/docker-desktop/)).
2. Create `C:\AgentWorkspace\inbox` and `C:\AgentWorkspace\outbox`.
3. Run n8n with the workspace folder mounted:
   ```powershell
   docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n -v C:\AgentWorkspace:/data docker.n8n.io/n8nio/n8n
   ```
4. Import `n8n-workflow/02-watch-and-summarize.json`, review each node against your n8n version, and set the workflow **Active**.
5. Drop a `.txt` file into `C:\AgentWorkspace\inbox` and check `C:\AgentWorkspace\outbox` a few seconds later.

Full explanations, reasoning, and troubleshooting are in [`article.md`](article.md) / the published Medium post.

## Stack used in this article

- **Ollama** (`llama3.2:3b`) — local LLM, free, offline
- **n8n** (Docker, with a mounted Windows folder) — no-code agent builder
- **Windows folders** as the trigger and output — no cloud storage needed

## Status

- [x] Automatic (non-manual) trigger built and tested
- [x] Docker volume mount reaching real Windows files
- [ ] Kubernetes deployment (a later article's own repo)

## License

MIT — see [LICENSE](LICENSE).
