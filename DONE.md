# The Impossible Fishbowl — Complete

## What Was Built

A real-time 3D aquarium ecosystem simulation running entirely in the browser as a single HTML file. The experience features a glass fishbowl with three species of fish governed by Craig Reynolds' Boids flocking algorithm, a self-balancing ecosystem with predator-prey dynamics, and multiple layers of visual effects.

## What Works

**Core Rendering**
- Glass fishbowl with fresnel transparency, chromatic edge tinting, and dual specular highlights
- Sandy floor with real-time procedural caustic light patterns (4-layer sine wave network)
- 4 volumetric god ray light shafts with pulsing animation
- Animated water surface with multi-frequency wave displacement and ripple patterns
- 250 floating plankton particles with additive blending
- Underwater atmosphere depth fog
- Slowly shifting background gradient
- Procedural rocks, branching coral, and swaying seaweed

**Fish System**
- 3 species: Neon Tetra (blue schooling), Angelfish (gold mid-tier), Betta (purple predator)
- Each fish built from procedural BufferGeometry with real-time spine undulation
- Animated tail fin, dorsal fin, and pectoral fins
- Smooth quaternion slerp rotation toward movement direction
- Full Boids: separation, alignment, cohesion, wall avoidance, vertical bounds

**Ecosystem**
- Food chain: large eats medium+small, medium eats small
- Predator avoidance and prey hunting behavior integrated into boids
- Reproduction: mature fish produce offspring that fade in
- Lifespan: old fish fade out and sink
- Population protection: minimum species counts enforced, respawn if needed
- Runs self-balancing for extended periods

**Interaction**
- Click/tap to drop food particles (3-5 per click, drift down, attract fish)
- Mouse hover near glass scatters nearby fish
- Drag to orbit, scroll to zoom
- Feed button for mobile
- Touch support for all interactions

**HUD**
- Frosted glass panel with population counts per species
- Day counter (1 real minute = 1 day)
- Animated hint overlay that fades after 8 seconds

## What I'd Improve With More Time

- **Post-processing**: Screen-space refraction through the glass bowl using render targets (would make the glass truly distort what's behind it)
- **Better fish geometry**: More detailed body profiles per species, flowing betta fins with cloth-sim-like vertex animation
- **Instanced rendering**: Move fish to InstancedMesh with custom vertex shader attributes for better performance at higher fish counts
- **Depth of field**: Fake bokeh blur for fish far from the focal plane using multi-pass rendering
- **Sound design**: Ambient underwater audio, subtle bubble sounds
- **Procedural plants**: Kelp with more segments and physics-based sway instead of simple rotation
- **Day/night cycle**: Gradually shift lighting color temperature, dim lights at "night"
- **Fish personality**: Give individual fish slightly different behavior weights (some braver, some more shy)
- **Bubble particles**: Rising bubbles from the sand/coral with refraction sprites

## How to View

```bash
open index.html
# or
python3 -m http.server 8888
# then visit http://localhost:8888
```

Works in Chrome, Firefox, Safari, or Edge. Best experienced fullscreen.
