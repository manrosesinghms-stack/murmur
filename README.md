# MURMUR ✨

*Guide a living swarm of light.* Move your cursor and hundreds of glowing motes flow after you like a starling murmuration — because they actually run flocking rules. A mesmerising, novel game for the browser (CrazyGames-bound), chosen for the highest viral ceiling among four concepts.

**Status: Phase 1 (the swarm core) — done & verified.** Mesmerising, and holds 200+ fps with 1000+ motes. See [MASTERPLAN.md](MASTERPLAN.md) for the full plan and next phases (the collect/grow/survive loop, identity + audio, ship).

## Run locally

```
python -m http.server 8260
```

Open http://localhost:8260 and move your cursor. Hold to gather the swarm tighter.

## How it works (single HTML file)

- **2D canvas + additive blending** with a feedback trail buffer (fade the frame instead of clearing) → light-painting for free, runs on every device incl. mobile.
- **Boids flocking** (separation / alignment / cohesion) + cursor attraction + a gentle swirl curl, over a **uniform spatial grid** (bucket agents, query 3×3 cells, cap neighbour checks) so it scales to thousands.
- **Perf:** Float32Arrays for pos/vel, one pre-rendered radial-glow sprite per palette hue, capped pixel ratio, and an auto-tune that trims the swarm if fps dips below 48.

## Debug hooks

`window.__mur` — `.info()` (count, fps, pointer), `.move(x,y,down)` (drive the pointer), `.setN(n)` (resize the swarm).
