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
- Two-player camera mode: stand on opposite sides of the view. Hands are assigned by palm position and can select targets in their own half. The equation and timer are shared; individual hit scores are separate from the combined arcade score. This is experimental, especially in classic modes where targets are shared.
- Teacher mode: enter one verified arithmetic equation per line, e.g. `7 × 8 = 56`. Supports nonnegative integer answers and single-operation equations. Custom questions apply to falling, stationary and memory modes, not Equation Rush.
- Progress dashboard: available on the main menu and directly on the end-of-round results screen. Shows rounds played, best score, average accuracy, latest score change, a chart of the last ten scores, and a filterable history table. Defaults to the just-played mode on results. Keeps the latest 100 rounds in browser local storage; export history as JSON. Compare rounds with similar settings.
- Round CSV: question, target/correct answer, selection, result, response time, player and hand.
- Camera movement summaries: normalized hand travel, approximate speed, and maximum horizontal screen reach. These are image-space estimates, not physical distances or calibrated biomechanics.
- Spotlight walkthrough: short contextual explanations highlight actual settings and controls, automatically scroll to each item, and support Back, Next, Skip, Escape and arrow-key navigation. Dropdowns use larger text and touch-friendly sizing.

## Tracking and privacy

MediaPipe Hand Landmarker estimates 21 landmarks per detected hand, with gameplay using the average of the wrist and four finger-base landmarks for a stable palm cursor. Right hand is selected by default; left hand and both hands are available in settings. No pose model is loaded. GPU initialization falls back to CPU. Hand tracking defaults to a faster adaptive One Euro filter (responsiveness 0.75), with selectable EMA or raw modes. Hand detection, presence and tracking confidence thresholds are 0.5; hand selection uses the model's handedness classification. Brief dropouts retain filter state without allowing collisions from invisible hands. Optional speed limiting is off by default; reacquisition takes 50 ms and answer hits have a 140 ms shared cooldown. Up to two hands are detected in solo play; multiplayer supports up to four when both hands are selected. Hand ownership is determined by screen half, not person identity. Camera processing occurs in the browser; no footage is intentionally uploaded or recorded by the game. The model, runtime and fonts are fetched from external hosts, so first load requires connectivity. Local scores and progress stay in the browser unless exported.

## Deploy

The repository is a static single-page application. In GitHub Settings → Pages, select Deploy from a branch, main, / (root). No server or API key is required. Camera use requires HTTPS and permission.

## Limitations

Hand estimates can jitter, especially with occlusion or poor lighting. Response time combines thinking and movement. Multiplayer uses screen halves rather than persistent person identity, and shares questions, timer and global collision cooldown. Browser/device camera performance requires live testing. Results are practice feedback rather than standardized assessments.

Falling bubbles disappear immediately when their lower edge reaches the screen bottom. Correct bubbles count as misses without a point deduction; distractors and expired power-ups disappear without penalty.
