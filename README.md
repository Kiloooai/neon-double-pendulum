# 🌀 Neon Double Pendulum

*Chaotic compound pendulum simulation. Drag to set initial angle, release and watch unpredictable, beautiful paths emerge in glowing neon. Adjust masses, lengths, gravity, friction, trail persistence. The butterfly effect, visualized.*

---

## What is this?

A double pendulum: a pendulum with another pendulum hanging from its bob. It's a classic example of a chaotic system — tiny changes in starting conditions lead to vastly different trajectories. The motion is governed by nonlinear differential equations and exhibits sensitive dependence on initial conditions (the "butterfly effect"). This neon-ified version shows the path of the second bob as a glowing trail, turning the chaos into luminous art.

---

## Features

- **Two-pendulum dynamics** with full Lagrangian mechanics (no approximations)
- **Real-time RK4 integration** for numerical stability
- **Neon glow** on both bobs and arms, plus a fading trail behind the lower bob
- **Interactive setup** — drag anywhere to set the starting angle of the first arm (second arm follows), release to start swinging
- **Adjustable parameters:**
  - Mass 1 & Mass 2 (0.5–3) — changing mass ratio alters behavior significantly
  - Length 1 & Length 2 (50–200 px) — affects periods and chaos intensity
  - Gravity (0.2–2) — global gravitational acceleration
  - Friction (0–0.05) — angular damping to eventually settle the pendulum
  - Trail fade (0.001–0.2) — controls how long the path persists; lower = longer trails
- **Reset** — stop and return to default starting position
- **Randomize** — randomize all parameters for new chaotic configurations
- **Energy readout** — monitors total mechanical energy (should be conserved without friction)
- **FPS counter**
- **Single HTML file** — no dependencies

---

## How to Use

1. Open `index.html`
2. **Click and drag** from anywhere on the canvas. The first arm will point toward your cursor. The second arm跟随s naturally.
3. **Release** to let the pendulum swing. Watch the lower bob trace a complex, unpredictable path.
4. Try slight variations in the drag angle — even a one-pixel difference produces completely different trajectories after a few seconds.
5. Use sliders to change the system:
   - **Masses** — unbalanced masses create more dramatic swings
   - **Lengths** — longer arms = slower, smoother arcs; different ratios produce distinct chaos patterns
   - **Gravity** — higher gravity = faster motion
   - **Friction** — add a little to eventually calm the system; set to 0 for perpetual motion (idealized)
   - **Trail Fade** — lower values keep trails longer, building intricate lacework; higher values give sharper motion blur
6. Press **Randomize** to explore new parameter combinations
7. Press **Reset** to stop and return to the default 90° starting angle

---

## Technical Details

- **Equations of motion** derived from the Lagrangian for a double pendulum with point masses, no friction:
  - General coordinates: angles θ₁, θ₂ measured from vertical (downward = 0)
  - Kinetic and potential energy → Euler-Lagrange equations → second-order ODEs
  - Converted to first-order system: state = [θ₁, θ₂, ω₁, ω₂]
  - Equations involve trigonometric coupling terms `sin(θ₂-θ₁)`, `cos(θ₂-θ₁)` and mass/length ratios
- **Numerical integration:** 4th-order Runge-Kutta (RK4) with fixed timestep `dt = 0.016s` (≈ 60 Hz)
- **Boundary:** Angles unbounded (wrapping handled by trig functions)
- **Rendering:** Canvas 2D. Arms drawn as lines; bobs as circles with `shadowBlur` for neon glow. Trail stored as array of points (max 500) drawn as a polyline. Background cleared each frame with semi-transparent black to produce fade effect.
- **Energy calculation:** `KE = ½ m v²` for each bob (velocities computed from angular velocities and geometry); `PE = -m g y` (y increases downward). Total energy should be constant absent friction.

---

## The Real Story

The double pendulum is the poster child for chaos theory. It's simple to build, impossible to predict. You can set it nearly identically twice and get entirely different dances. The trail visualization turns that unpredictability into something beautiful — like watching a neon ghost write calligraphy that no one could ever replicate. Fiddle with the mass ratios: when the lower bob is heavier, it dominates; when the upper is heavier, it drives the show. Add a little friction and watch the chaos slowly settle into a quiet swing. It's physics with personality.

---

*Made with 🌀 and numerical integration.*

**Repo:** https://github.com/Kiloooai/neon-double-pendulum
