# Copilot instructions

## Project structure and architecture

- This is a single-page, dependency-free quiz. `index.html` is the entry point and contains the markup, styles, question data, and application logic; open it directly in a browser.
- The `questions` array is the quiz's source of truth. `renderQuestion()` draws the current prompt and answers, `selectAnswer()` handles scoring and feedback, and `showResults()` chooses the final reaction and celebration.
- Keep progress, score, feedback, and results in sync with the current question state. Restart should reset the state and return focus to the first answer.

## Build, test, and lint

- There are no build, test, or lint scripts or external dependencies. No install or server is needed; open `index.html` in a browser to run the app.
- There is no automated single-test command. Manually smoke-test the affected flow in a browser: answer questions, check progress and score for right and wrong answers, complete the quiz, and replay. Use Tab, Enter, and Space to verify keyboard operation.

## Code conventions

- Keep the app self-contained in `index.html` unless the project is intentionally changing its no-build, no-dependency setup.
- Add quiz content as objects in `questions` with `question`, `answers`, zero-based `correct`, and explanatory `fact` fields. Keep the correct index aligned with the answer list.
- Use the existing state-driven rendering and DOM APIs (`textContent`, `replaceChildren`, and event listeners) for dynamic quiz content.
- Preserve semantic controls and accessibility behavior: answer buttons, progressbar values, live feedback/results, descriptive answer labels, visible `:focus-visible` states, and focus handoffs between answers, Next, question headings, and replay.
- Preserve the `prefers-color-scheme` theme tokens and `prefers-reduced-motion` handling when changing styles or animations. Decorative stars and celebration effects should not add screen-reader noise.
- Keep result tiers and high-score celebration thresholds coordinated in `showResults()` and the `.is-celebrating` styles.
