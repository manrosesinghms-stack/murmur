# MURMUR — Master Plan

*(working title; alts: Wisp, Starling, Luma)*

A mesmerising game about guiding a living swarm of light. Chosen over three other magical concepts for the **highest viral ceiling**: it wins the 10-second-clip test, is watchable + playable, has the lowest skill floor and broadest appeal, and is genuinely unseen as a *scored game* (fluid sims already exist as famous toys; a murmuration you score with basically doesn't).

## The fantasy

You are the wind. You guide a living swarm of glowing motes through a dark, beautiful world. It moves like a real starling murmuration — flowing, splitting, reforming — because it actually runs flocking rules (separation, alignment, cohesion) plus attraction to your cursor. It is alive, and it is yours.

## Core mechanic

- **Move → the living cloud follows.** The swarm is gently drawn to your pointer but flocks, so it never collapses to a dot — it ribbons, spirals, and swirls. Instantly readable in 2 seconds, no tutorial.
- Skill expression: good players *sculpt* the swarm — whip it through tight gaps, fan it wide to sweep, coil it to dodge.

## The loop (one-more-run)

1. **Collect:** scattered lights drift in the dark. Sweep your swarm over them → absorb → the swarm **grows** (more agents = more spectacular, higher score multiplier).
2. **Survive:** the dark is alive — creeping shadow, voids, and predators pick off stragglers at the swarm's edges. Lose too many and the run ends.
3. **Score & restart:** score = lights gathered × swarm size × distance. Clear end screen, instant restart. Escalates: denser lights, denser danger, the world opens up.

## Why it can go viral

- **Clip-viral:** a glowing murmuration swallowing lights and fleeing a shadow is r/oddlysatisfying / TikTok / Shorts catnip. Every session is a screenshot.
- **Watchable:** streamers/creators can't resist hypnotic emergent motion = free marketing.
- **Universal:** all ages, no genre barrier, low floor / high ceiling.
- **Novel:** press/creator interest because it's not a clone of anything on the platform.

## Technical plan

- **Single HTML file.** Start with **2D canvas + additive blending** (not WebGL): a feedback trail buffer (fade the frame instead of clearing) gives gorgeous light-painting for free, runs on every device incl. mobile, and 800–1500 glowing trailed boids already looks stunning. Port the hot path to WebGL points only if we need 10k+.
- **Flocking optimized** with a uniform spatial grid (bucket agents by cell, query 3×3 neighbourhood, cap neighbour checks) → scales to thousands.
- **Perf discipline:** Float32Arrays for pos/vel; a single pre-rendered radial-glow sprite drawn per agent (no per-agent gradients); capped pixel ratio; agent count auto-tunes to hold 60fps.
- **Feel:** color shifts by speed/size/biome; overlaps bloom white-hot via `lighter` compositing; generative ambient audio (WebAudio) that responds to swarm state.

## Phases

- **Phase 1 — Swarm core (make-or-break, building now):** hundreds of glowing boids that flock + follow the cursor, with fading light-trails. Prove it's mesmerising AND holds 60fps. Everything rides on this.
- **Phase 2 — The loop:** lights to absorb, swarm growth, the encroaching dark/predators, score, game over, instant restart.
- **Phase 3 — Identity & juice:** color/biome shifts, sculpting gates, generative audio, title/menus, bloom pulses, screenshot-worthy moments.
- **Phase 4 — Ship:** CrazyGames SDK, mobile touch, perf pass on low-end, cover art + gameplay video (reuse the Super Keeper capture→ffmpeg pipeline), submit.

## North star

Someone films their screen without being asked. If a stranger sees a clip and thinks *"I need to touch that,"* we've won.
