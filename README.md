# MathReact

**Move. Think. React.** A browser-based math game that combines mental math with movement, reaction and hand-eye coordination.

## Play

[Open MathReact](https://aaron-ragsdale.github.io/MathReact/) (available once GitHub Pages is enabled).

1. Choose timed or untimed practice, difficulty, starting level and math focus.
2. Select **Play with camera** and allow camera access, or choose mouse/touch mode.
3. Stand far enough from the camera for your hands to be visible. Reach toward the correct answer bubble using either selected hand. In mouse/touch mode, move or touch the pointer over the answer.
4. Earn points and build streaks. Every eight correct answers advances the level until Champion.
5. Review your mistakes or export your results as CSV at the end of the round.

## Game features

- Six progressive levels, from basic arithmetic to multi-operation expressions (grade labels are approximate, not formal curriculum alignment).
- Addition, subtraction, multiplication and division focus modes, or automatic level progression.
- Easy, medium and hard difficulty; relaxed, normal and fast bubble speeds.
- Timed rounds of 30, 60, 90 or 120 seconds, and untimed practice.
- Optional power-ups and hazards: freeze, extra time, double points, bombs, fog and speed boosts.
- Left, right or both hands; adjustable smoothing; corner, background or hidden camera preview.
- Pause and resume using the button or Space. Switching browser tabs pauses play.
- Local personal best scores, accuracy, missed-question review and CSV export.

## How computer vision works

MathReact uses MediaPipe Pose Landmarker Full, which estimates 33 body landmarks for one person. Only the hand landmarks drive gameplay: left pinky/index/thumb (17, 19, 21) and right pinky/index/thumb (18, 20, 22). Each hand cursor is the mean of its three coordinates. Wrist and hand visibility checks reject unreliable detections. Exponential moving average (EMA) filtering reduces jitter; a higher responsiveness value reduces smoothing. Camera coordinates are mirrored for intuitive movement. A short collision cooldown reduces accidental consecutive hits.

The model runs in the browser, attempting GPU acceleration first and falling back to CPU. No separate Hand Landmarker model is used. Pose-based hand positions are approximate, not precise finger tracking.

## Privacy and requirements

Camera frames are processed locally and are not intentionally uploaded or recorded by the application. The page downloads MediaPipe, model assets and fonts from external hosts, so initial internet access is required. Personal best scores use browser localStorage; the CSV is saved only when requested. Camera tracks stop at the end of a round. Use a modern browser with camera permission and HTTPS for camera mode. Mouse/touch mode works without granting camera access.

CSV rows contain the question, correct answer, selected answer, result and elapsed question time in seconds (excluding manual pauses). This measures time since question presentation, not isolated motor reaction time. Accuracy includes correct selections, wrong selections and missed questions.

## Publish using GitHub Pages

Place `index.html` and `README.md` in the repository root. In GitHub, open **Settings → Pages → Deploy from a branch**, select the default branch and `/ (root)`, then save. Open the Pages URL shown by GitHub. No server, API key or build step is required.

## Repository structure

- `index.html` — game interface, arithmetic generator, rendering, camera inference and scoring.
- `README.md` — instructions and technical overview.

## Classroom ideas

Try untimed practice before timed rounds, focus on one operation, compare smoothing settings, or discuss the difference between solving a problem and physically reaching its answer. Use mouse/touch as an alternative input method. Results are practice feedback, not a standardized assessment.