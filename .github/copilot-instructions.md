# Copilot instructions

## Project structure and architecture

- `index.html` is the entire application: semantic page structure, inline CSS, the question dataset, and the quiz controller are all in this file. It is a static page; open it directly in a browser.
- The quiz controller owns the current question, score, and answered state. `renderQuestion()` updates the question and creates answer buttons; `selectAnswer()` locks in a response, updates score/progress, and displays feedback; `showResults()` switches to the results screen. Keep these UI updates consistent when changing quiz behavior.
- Each question is an object in the `questions` array with a category, prompt, options, correct option index, and fact shown after answering. The result message and emoji are selected by score in `showResults()`.
- Theme colors are CSS custom properties in `:root` and its `prefers-color-scheme: dark` override. Use those tokens for shared colors so the light and dark themes stay coordinated.

## Build, test, and lint

- There are no configured build, test, or lint commands or dependencies.
- To run the app, open `index.html` directly in a browser; no server or build step is required.
- There is no automated single-test command. For a browser check, exercise correct and incorrect answers, score and progress updates, question navigation, results, and restart. Check keyboard focus and both system color schemes when changing UI or interaction behavior.

## Codebase conventions

- Keep the app dependency-free and self-contained in `index.html`; do not introduce a framework, bundler, or server requirement for ordinary quiz changes.
- Quiz data is kept separate from rendering and interaction logic in the `questions` array. Use the existing question fields and zero-based answer indices when adding or editing questions.
- Answers and actions are native buttons. Preserve their accessible names, visible keyboard focus, disabled-after-selection behavior, and the existing live feedback/progress announcements.
- Respect `prefers-reduced-motion`; keep feedback meaning clear beyond color alone, with explanatory text and the existing correct/wrong states.
