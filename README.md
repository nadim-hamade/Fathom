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
| B | Autopilot — a trained agent flies the sub (see below) |

## Watch the AI play

Press **B** to hand the sub to a neural network that learned to play from scratch — it steers to the gate by ear, spends sonar only when it's genuinely lost, and dives as deep as it can. It's a PPO agent trained by self-play in a headless port of this exact game; the trained weights ship here as `policy.json`. Write-up, training curves, and code: [fathom-rl](https://github.com/nadim-hamade/fathom-rl).

## Design constraints

The premise is protected by three rules: all art is procedural and all audio synthesized — no asset files, ever; every tunable lives in the `CFG` object at the top of `index.html`; and nothing is ever visible on screen that wasn't paid for with sound or proximity — no minimap, no persistent map memory.

## Status

Playable — the descent loop (ping-to-see, oxygen, lurkers, exit-gate hum), consumables, biomes, and deep-zone hazards are complete and verified in the browser, plus a trained-agent autopilot. Palette is three locked accents on near-black; targets 60fps with no per-frame allocations in the update path.
