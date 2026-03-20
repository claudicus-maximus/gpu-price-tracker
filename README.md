# GPU Price Tracker 🇨🇦

Tracks used GPU prices (16GB+ VRAM) from Canadian subreddits:
- [r/CanadianHardwareSwap](https://reddit.com/r/CanadianHardwareSwap) — used/second-hand
- [r/bapcsalescanada](https://reddit.com/r/bapcsalescanada) — deals/sales

## How it works

1. **Scraper** runs 3x daily via cron (9am, 2pm, 8pm ET)
2. **Price extraction**: regex for obvious formats, [ollama](https://ollama.com) (gemma3:4b) for ambiguous posts
3. **GPU model normalization**: maps variants to standard names (e.g. "EVGA RTX 3090 FTW3 Ultra" → "RTX 3090")
4. **SQLite database** stores every price point
5. **Static dashboard** reads `data.json` for visualization

## Files

- `index.html` — interactive dashboard (Chart.js)
- `data.json` — exported price data (auto-updated)
- `gpu_prices.db` — SQLite database with all listings

## Tracked GPUs

NVIDIA: RTX 5090, 5080, 4090, 4080 (Super), 4070 Ti (Super), 4070 Super, 4060 Ti 16GB, 3090 (Ti), 3080 (Ti), A6000, A5000, A4500

AMD: RX 9070 XT, 7900 XTX, 7900 XT, 7800 XT, 6900 XT, 6800 XT

Intel: Arc B580
