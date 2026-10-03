# Daily Learn for Firefox

Type any topic and get a cited, plain-language briefing built from free sources (Wikipedia, research papers, news, web pages, YouTube), written by the model you choose: OpenRouter, LM Studio or Ollama. Needs Firefox 140 or newer (desktop).

## Try it now (temporary)
1. Open `about:debugging#/runtime/this-firefox`.
2. **Load Temporary Add-on...** and pick `manifest.json` in this folder.
3. Temporary add-ons are removed when Firefox restarts, and your saved briefings go with them.

## Install permanently (free)
Release Firefox only keeps signed add-ons. Signing is free and automatic for add-ons you don't publish:
1. Zip the folder contents (so `manifest.json` is at the top level), or use `daily-learn-firefox.zip`.
2. Go to addons.mozilla.org/developers, sign in, **Submit a New Add-on**, choose **On your own** (unlisted).
3. Download the signed `.xpi` after the automatic check and open it in Firefox.
Alternatively, Firefox Developer Edition / Nightly / ESR can run unsigned add-ons if you set
`xpinstall.signatures.required` to `false` in `about:config`.
Change the `id` in `manifest.json` (`daily-learn@local.example`) to your own before signing.

## Pick a model (Settings > Language model)
The setup screen opens on first install. Each provider has an ordered model chain: if the first model fails or is
rate-limited, the next takes over. "Test connection" sends one tiny request to check the key, address and model.

| Provider | What you need |
|---|---|
| **OpenRouter** | A free key from openrouter.ai/keys. Defaults to `openrouter/free`. "Load model list" to browse; "Only list free models" is on by default. |
| **LM Studio** | Load a model, open the Developer tab, start the server (`http://localhost:1234/v1`), then click "Detect models". |
| **Ollama** | `ollama serve` running (`http://localhost:11434`) and a pulled model, then "Detect models". No `OLLAMA_ORIGINS` setup needed. |

For small local models, lower "Evidence per call" (try 6000) and use Quick depth.

## Using it
- Click the toolbar icon: type a topic, or "Surprise me" (your interests list first, then Wikipedia's featured
  article, on-this-day or a random article; never repeats).
- Choose reader level and depth on the home screen. A briefing takes a minute or two; keep the tab open.
- Briefings are saved in your browser and listed in the sidebar. Export as Markdown, HTML, Anki cards, sources JSON,
  copy, or print to PDF. Optional daily-topic reminder under Settings > Daily topic.
- Adult content is filtered out (strict safe-search plus a content filter).

## Permissions
Firefox may ask you to approve "access your data for all websites" on install. If it doesn't, open
`about:addons` > Daily Learn > Permissions and switch on the site access. Without it, sources and local models can't be reached.

## Differences from Chrome
- Local-server headers (Ollama / LM Studio) and DuckDuckGo/YouTube headers use Firefox's webRequest instead of
  declarativeNetRequest. The rule is registered by the app tab, so keep it open during a run (you have to anyway).
- Not yet verified in a live Firefox: Ollama/LM Studio connections, DuckDuckGo search and YouTube transcripts.
  If one fails, the run notes show which.
