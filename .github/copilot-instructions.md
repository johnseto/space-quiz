# Copilot instructions

## Project structure and architecture

The app is a standalone `index.html`: HTML, CSS, quiz content, and JavaScript are all kept together so the page can run directly from `file://` without a server, build step, or external dependencies.

- The markup defines the quiz, progress and score display, answer feedback, and results/restart screen. The UI is updated by targeting stable element IDs.
- The inline stylesheet contains the complete visual system, including responsive layout, light/dark color-scheme variants, feedback animations, and reduced-motion support.
- The inline script owns the `questions` data, current-question and score state, rendering, answer selection, progression, and restart. Each question's `answer` is a zero-based index into its `options` array.

When changing quiz behavior or adding questions, keep the question data and its answer indices consistent with the rendering and scoring flow. Preserve the single-file, no-dependency setup unless the project requirements change.

## Build, test, and lint

There is no package manifest, build command, automated test runner, or linter. The page runs directly in a browser. For a manual smoke test, open `index.html` (or use the integrated browser on its `file://` URL) and check keyboard focus through the answer buttons, both correct and incorrect feedback, score and progress updates, completion results, and restart.

## UI and interaction conventions

- Use native buttons for answer and navigation actions; keep them keyboard-operable and retain visible `:focus-visible` styling.
- Keep score and answer feedback announced through the existing live regions. Keep the progress bar's accessible value in sync with its visible progress.
- Respect `prefers-color-scheme` and `prefers-reduced-motion` when adding styles or animations.
- Render question and answer copy as text rather than treating quiz content as HTML.
