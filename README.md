# Free Ollama API via Colab for OpenCode

<p align="center">
  <img src="https://img.shields.io/badge/Status-Working-green?style=flat" alt="Status">
  <img src="https://img.shields.io/badge/Cost-100%25%20Free-brightgreen?style=flat" alt="Cost">
  <img src="https://img.shields.io/badge/License-MIT-blue?style=flat" alt="License">
</p>

> **Problem:** I have a weak/low-spec PC but want AI to help with coding.
>
> **Solution:** Run powerful LLMs on Google Colab (free GPU), expose via Cloudflare Tunnel, use in OpenCode - completely free!

---

## Why This?

| Your PC | With This Setup |
|---------|----------------|
| No GPU / Slow CPU | Uses Colab's free GPU |
| Can't run LLMs | 3 powerful models tested |
| Expensive API costs | 100% free forever |
| Limited to code snippets | Actually executes tools |

---

## How It Works

```
┌─────────────┐     ┌───────────────────┐     ┌──────────────┐     ┌─────────┐
│   Your PC   │────▶│  Cloudflare       │────▶│   Google    │────▶│   LLM   │
│  (OpenCode) │     │  Tunnel (Public)  │     │   Colab     │     │ (Qwen3) │
└─────────────┘     └───────────────────┘     └──────────────┘     └─────────┘
     ▲                                                              │
     │                                                              │
     └──────────────────────────────────────────────────────────────┘
                              OpenCode AI Response
```

---

## Quick Setup (3 Steps)

### Step 1: Run on Google Colab

1. Go to [Google Colab](https://colab.research.google.com)
2. Click **New Notebook**
3. Upload or copy code from `opencode_final.ipynb`
4. **Enable GPU:**
   - Go to **Runtime** → **Change runtime type**
   - Select **T4 GPU** → Click **SAVE**
5. Run all cells
6. Wait for tunnel URL (appears as `https://xxx.trycloudflare.com`)

### Step 2: Get Your API URL

```
Output: https://random-name.trycloudflare.com
        └────────── Add /v1 ──────────┘
API URL: https://random-name.trycloudflare.com/v1
```

Copy this! You'll need it for config.

### Step 3: Configure OpenCode

On your PC:

```
1. Create folder: C:\Users\<YOU>\.config\opencode\
2. Copy opencode.json to that folder
3. Replace YOUR-TUNNEL-URL with your actual URL
4. Copy AGENTS.md to the same folder
5. Start OpenCode and enjoy! 🎉
```

---

## 3 Tested Models

| Model | Context | Notes |
|-------|---------|-------|
| `qwen3.5-9b-32k` | 32K | **BEST** - Fast, great code generation |
| `qwen3-8b-32k` | 32K | Good alternative |
| `gemma4-e4b-32k` | 32K | Slower but better error messages |

All 3 support tool calling in OpenCode!

---

## Files

```
├── opencode_final.ipynb  # Main Colab notebook (run this)
├── opencode.json        # OpenCode config template
├── AGENTS.md         # System prompt
├── LICENSE          # MIT License
└── README.md        # This file
```

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Tunnel URL not showing | Wait 60s, enable T4 GPU first |
| Out of memory | Use only 1-2 models |
| Connection refused | Re-run notebook (session expired) |
| Tools not executing | Make sure URL ends with `/v1` |
| Ollama not responding | Run `!pkill ollama` in new cell |

---

## Important Notes

### For Users (Copy & Read)

- **Keep Colab running** - Tunnel works only while Colab is active
- **Use `/v1`** - API won't work without this suffix
- **GPU required** - CPU too slow for LLMs
- **Get fresh URL each session** - Old URLs expire

### Contributing

Found a bug or improvement? Open an issue or pull request!

---

## Cost: $0

- Google Colab Free: ✅
- Cloudflare Tunnel: ✅  
- Ollama: ✅
- OpenCode: ✅
- This repo: ✅

Everything is free forever!

---

## Credits

- [Ollama](https://ollama.com) - Local LLM runtime
- [OpenCode](https://opencode.ai) - AI coding assistant
- [Cloudflare](https://cloudflare.com) - Free tunnel
- [Google Colab](https://colab.research.google.com) - Free GPU

---

## License

MIT License - See [LICENSE](LICENSE) file.

---

<p align="center">
⭐ Star this repo if it helped you! ⭐
</p>