# MathReact

**Move. Think. React.** A browser-based math arcade combining mental math with physical movement.

## [Play MathReact](https://aaron-ragsdale.github.io/MathReact/)

Open the game on a camera-equipped device, select a game style and settings, and choose camera or mouse/touch play. Stand far enough back to keep your hands visible. Clear your play area.

## Game styles

| Style | Objective |
| --- | --- |
| Falling Answers | Solve the displayed equation and reach for its answer. |
| Equation Rush | Catch as many expressions as possible matching the displayed target. Multiple correct expressions may appear simultaneously. Target changes every 10, 15, 20 or 30 seconds; old bubbles clear at each change. |
| Stationary Targets | Solve the equation and select a fixed target. |
| Memory Math | View the equation for two seconds, then select the answer from memory. |

Choose timed (30–120 seconds) or untimed practice, arithmetic focus, starting level, difficulty, speed, hands, camera view, smoothing, sound and power-ups. Space pauses or resumes a round.

## Additional features

- Adaptive difficulty: after eight selections, difficulty increases at 87.5% correct or higher and decreases at 50% or lower.
- Two-player camera mode: stand on opposite sides of the view. Players are assigned by shoulder midpoint and can select targets in their own half. The equation and timer are shared; individual hit scores are separate from the combined arcade score. This is experimental, especially in classic modes where targets are shared.
- Teacher mode: enter one verified arithmetic equation per line, e.g. `7 × 8 = 56`. Supports nonnegative integer answers and single-operation equations. Custom questions apply to falling, stationary and memory modes, not Equation Rush.
- Progress dashboard: keeps the latest 100 rounds in browser local storage; export history as JSON.
- Round CSV: question, target/correct answer, selection, result, response time, player and hand.
- Camera movement summaries: normalized hand travel, approximate speed, and maximum horizontal screen reach. These are image-space estimates, not physical distances or calibrated biomechanics.
- Quick walkthrough: four short steps explaining settings, controls and results.

## Tracking and privacy

MediaPipe Pose Landmarker Full estimates 33 body landmarks, with gameplay using the mean of thumb, index and pinky positions for each hand. GPU initialization falls back to CPU. Visibility filtering, adjustable EMA smoothing and a 300 ms shared hit cooldown help reduce false hits. Two poses are enabled for experimental multiplayer. Camera processing occurs in the browser; no footage is intentionally uploaded or recorded by the game. The model, runtime and fonts are fetched from external hosts, so first load requires connectivity. Local scores and progress stay in the browser unless exported.

## Deploy

The repository is a static single-page application. In GitHub Settings → Pages, select Deploy from a branch, main, / (root). No server or API key is required. Camera use requires HTTPS and permission.

## Limitations

Pose estimates can jitter, especially with occlusion or poor lighting. Response time combines thinking and movement. Multiplayer uses screen halves rather than persistent person identity, and shares questions, timer and global collision cooldown. Browser/device camera performance requires live testing. Results are practice feedback rather than standardized assessments.
