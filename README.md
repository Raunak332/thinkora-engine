# thinkora-engine

Render engine for the Thinkora reel routine (mascot Orbi, v2 varied-shot style). Private.

The engine is stored as `thinkora-engine-bundle.b64.rtf`: an RTF export of a base64 tar.gz (35,755 bytes once decoded, gzip magic `1f8b08`).

## Restore

```bash
git clone --depth 1 https://github.com/Raunak332/thinkora-engine.git engine
cd engine
python3 -c "import re,base64;t=open('thinkora-engine-bundle.b64.rtf',encoding='latin-1').read();t=re.sub(r'\\\\[a-zA-Z]+-?\d* ?','',t[t.index('H4sI'):]);b=re.match(r'[A-Za-z0-9+/]*=*',re.sub(r'[^A-Za-z0-9+/=]','',t)).group(0);open('bundle.tar.gz','wb').write(base64.b64decode(b))"
tar xzf bundle.tar.gz   # creates ./bundle
```

No project-doc attachment needed. Scheduled runs can reach this repo only if it is attached to the routine.

## What's in ./bundle

- `engine/`: project template (`index.html`, `src/main.js`, `src/core/*.js` incl. `captions.js`, `tools/capture.mjs`, `tools/mix.py`). Add `script.json`, `data/` and `src/shots.js` per reel.
- `scripts/`: `voice.py`, `voice_x.py` (Kokoro voice), `align.py` (word timing), `estimate.py`, `setup.sh`, `py`.
- `examples/`: `shots.js` from three finished reels (planets/dusk, penny/copper, moon/night) and a `script.json`.

`scripts/words.py` (Whisper word timing) is referenced by the engine but is NOT in the bundle; use `align.py` (captions are estimated, about +/-0.15 s).

Font: Inter Black must be installed, or put `Inter-Black.otf` in `engine/fonts/`.

## Fixes

Commit any engine fix made during a run (for example `bundle/engine/src/core/captions.js`) back to this repo.
