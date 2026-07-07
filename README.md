# FATHOM — a sonar descent

A one-file browser roguelite. The ocean trench is pitch black; your sonar ping is the only way to see — it traces the cave walls as glowing contours that fade back into darkness. **Every ping also wakes the things living down there.** Manage oxygen, follow the exit gate's hum, descend forever.

Zero assets: all visuals are procedural Canvas 2D, all audio is synthesized WebAudio. One HTML file.

## Run

```
node dev-server.cjs        # → http://localhost:5317
```

Or any static server (`npx serve .`), or open `index.html` directly — there are no build steps and no network calls except the Fontshare font.

## Controls

| Input | Action |
|---|---|
| WASD / arrows | Thrust (full throttle is *loud* — nearby lurkers hear you) |
| Space / click | Sonar ping |
| P / Esc | Pause |
| M | Mute |

## Design constraints

The premise is protected by three rules: all art is procedural and all audio synthesized — no asset files, ever; every tunable lives in the `CFG` object at the top of `index.html`; and nothing is ever visible on screen that wasn't paid for with sound or proximity — no minimap, no persistent map memory.

## Status

Playable MVP — the core descent loop (ping-to-see, oxygen, lurkers, exit-gate hum) is complete and verified in the browser. Palette is three locked accents on near-black; targets 60fps with no per-frame allocations in the update path.
