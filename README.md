# Free API with Ollama through Colab and use in OpenCode

## The Problem

I have a **weak/low-spec PC** (no GPU, slow CPU, limited RAM) but want to use AI to help with coding. Running LLMs locally is too slow or impossible on my machine.

## The Solution

Run powerful LLMs on **Google Colab** (free GPU!), expose the API via **Cloudflare Tunnel**, and use it in **OpenCode** - completely free!

---

## Quick Setup (3 Steps)

### Step 1: Run Notebook on Google Colab

1. Go to [Google Colab](https://colab.research.google.com)
2. Click **New Notebook**
3. Copy all code from `opencode_final.ipynb` and paste into cells
4. **Important - Enable GPU:**
   - Click **Runtime** > **Change runtime type**
   - Select **T4 GPU** (or any GPU available)
   - Click **SAVE**
5. Run all cells sequentially
6. Wait for tunnel URL output (looks like `https://xxxx.trycloudflare.com`)

### Step 2: Get Your API URL

The notebook will output a URL like:
```
https://random-name.trycloudflare.com
```

**Add `/v1` at the end** to get your API URL:
```
https://random-name.trycloudflare.com/v1
```

Copy this URL - you'll need it for OpenCode config!

### Step 3: Configure OpenCode

**On your PC:**

1. Create folder: `C:\Users\<YOUR-USERNAME>\.config\opencode\`
2. Copy `opencode.json` to that folder
3. Open `opencode.json` in a text editor
4. Replace `YOUR-TUNNEL-URL` with your actual URL from Step 2
5. Copy `AGENTS.md` to the same folder

---

## Colab Configuration Details

### How to Enable GPU (T4):

1. Open your Colab notebook
2. Click **Runtime** (top menu)
3. Click **Change runtime type**
4. Under "Hardware accelerator" - select **T4 GPU**
5. Click **SAVE**
6. Run your cells

### Runtime Types Available:

| Runtime | GPU | Memory | Notes |
|---------|-----|--------|-------|
| T4 | 16GB | ~16GB | ✅ Recommended |
| V100 | 32GB | ~32GB | May not be available |
| A100 | 40GB | ~40GB | Rarely available |
| CPU | None | ~12GB | ❌ Too slow for LLMs |

### If T4 not available:

- Wait a few minutes and try again
- Colab free tier allocates GPUs dynamically
- Try at different times of day

---

## 3 Working Models (Tested & Verified)

| Model | Context | Best For |
|-------|---------|----------|
| qwen3.5-9b-32k | 32K | **BEST** - Fast, great coding |
| qwen3-8b-32k | 32K | Good alternative |
| gemma4-e4b-32k | 32K | Slower, better errors |

All 3 models support tool calling in OpenCode!

---

## Files Included

| File | Description |
|------|-------------|
| `opencode_final.ipynb` | Main Colab notebook |
| `opencode.json` | OpenCode config template |
| `AGENTS.md` | System prompt |
| `README.md` | This file |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Tunnel URL not showing | Wait 60 seconds, make sure GPU is enabled |
| Out of memory error | Use only 1-2 models instead of 3 |
| Connection refused | Re-run notebook (Colab session may have expired) |
| Model not executing tools | Make sure URL ends with `/v1` |
| Ollama not responding | Run `!pkill ollama` then restart |

---

## How It Works (Technical)

```
Your PC (OpenCode)
       |
       v
Cloudflare Tunnel (free public URL)
       |
       v
Google Colab (free GPU + Ollama)
       |
       v
LLM (Qwen3.5-9B / Qwen3-8B / Gemma4)
```

---

## Cost: **$0**

- Google Colab Free: ✅
- Cloudflare Tunnel: ✅
- Ollama: ✅
- OpenCode: ✅

Everything is free forever!

---

## Credits

- [Ollama](https://ollama.com) - Local LLM runtime
- [OpenCode](https://opencode.ai) - AI coding assistant
- [Cloudflare](https://cloudflare.com) - Free tunnel service
- [Google Colab](https://colab.research.google.com) - Free GPU

---

## License

Free to use, modify, and share!