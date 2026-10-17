# Agent World

**Only working together can problems be sorted.**

A multi-agent scientific research console that runs in the browser.

- Talk to **one** endpoint, or query **many** in parallel  
- Compare answers side-by-side  
- **Synthesize** them into a single stronger resolution  
- Scientific workflows + specialist roles (Methodologist, Skeptic, Synthesizer, …)  
- Evidence log and session export (JSON + Markdown)  
- Optimized for desktop and **iPhone Pro Max** (Add to Home Screen)

> No interface can reach every private AI on Earth. This console only queries the API endpoints **you** configure and authorize.

---

## Quick start

1. Open `index.html` in a modern browser (or deploy the folder to GitHub Pages / any static host).
2. Click **＋ Add** and connect at least one OpenAI-compatible, Ollama, or Anthropic-style endpoint you control.
3. For multi-agent work: switch to **Multi-agent**, select several endpoints (green checks), send one question.
4. Review the reply cards, then click **Synthesize & resolve**.

### Local demo (no server required)

```bash
# Optional: serve the folder so the web manifest and icons load cleanly
npx serve .
# or
python -m http.server 8080
```

Then open the URL on your phone or desktop.

---

## iPhone Pro Max — Add to Home Screen

1. Open the site in **Safari** on your iPhone.
2. Tap the **Share** button → **Add to Home Screen**.
3. Confirm the name **Agent World**.
4. The app opens full-screen with the custom icon.

**Icon files** (in `icons/`):

| File | Size | Use |
|------|------|-----|
| `icon.svg` | vector | Sharp at any size, favicon |
| `apple-touch-icon.png` | 180×180 | iOS home screen (required) |
| `icon-192.png` | 192×192 | PWA / Android |
| `icon-512.png` | 512×512 | PWA install / splash |

> If the PNG files are missing, Safari still works; generate them from `icon.svg` (see below).

### Generate PNG icons from the SVG

```bash
# With ImageMagick or rsvg-convert
rsvg-convert -w 180 -h 180 icons/icon.svg -o icons/apple-touch-icon.png
rsvg-convert -w 192 -h 192 icons/icon.svg -o icons/icon-192.png
rsvg-convert -w 512 -h 512 icons/icon.svg -o icons/icon-512.png
```

Or open `icons/icon.svg` in a browser / design tool and export the sizes above (full-bleed, no transparency for the 180px iOS icon).

---

## Multi-agent flow

```
Your question
    ↓
[ Scientific workflow + optional roles ]
    ↓
Parallel calls to every selected endpoint
    ↓
Side-by-side answer cards
    ↓
Synthesize & resolve  →  one improved answer
```

**Roles** (prompt injectors): Methodologist, Skeptic, Evidence synthesizer, Data extractor, Hypothesis engineer, Statistical interpreter.

**Workflows**: Direct, Hypothesis, Literature plan, Appraisal, Methods critique, Independent review, Structured extract, Uncertainty.

---

## GitHub Pages deploy

1. Create a new repository (e.g. `agent-world`).
2. Upload the contents of this folder (`index.html`, `manifest.webmanifest`, `icons/`, `README.md`).
3. Settings → Pages → Source: Deploy from branch `main` / root.
4. Visit `https://<user>.github.io/agent-world/`.

For production API keys, put a small proxy behind your own backend — never embed valuable keys in a public static page (CORS and key exposure).

---

## Security notes

- API keys entered in the UI stay in **page memory for the current session only**. They are not written to `localStorage`.
- Browser **CORS** often blocks direct calls to third-party APIs. Use local models (Ollama), OpenRouter with a proxy, or your own backend.
- Directory entries (ChatGPT, Claude, Elicit, PubMed, …) are **external links** only. They do not receive prompts from this page.

---

## License

MIT — use, modify, and share freely. Prefer primary sources; report uncertainty.
