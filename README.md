# Your First No-Code Agent: Automating a Daily Task with n8n + Ollama

Standalone companion repo for the Medium article of the same name. This repo is self-contained — it doesn't depend on, or link to, any other article's repo.

📖 Medium article: https://medium.com/@babul_b/automating-a-daily-task-with-n8n-ollama-cd4c7b438117

## What's in this repo

| File | What it is |
|---|---|
| [`n8n-workflow/02-watch-and-summarize.json`](n8n-workflow/02-watch-and-summarize.json) | The exact workflow built in the article — import via n8n's **Menu → Import from File** |

## Stack used in this article

- **Ollama** (`llama3.2:3b`) — local LLM, free, offline
- **n8n** (Docker, with a mounted Windows folder) — no-code agent builder
- **Windows folders** as the trigger and output — no cloud storage needed

## Status

- [x] Automatic (non-manual) trigger built and tested
- [x] Docker volume mount reaching real Windows files

## License

MIT — see [LICENSE](LICENSE).
