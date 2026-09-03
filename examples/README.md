# Examples

Interfaces built with the `ux-laws` skill loaded, kept here so the laws can be read against real
output instead of in the abstract.

Each example is a single self-contained HTML file — open it directly in a browser, no build step.

The tic-tac-toe demo is the site's landing page, so it lives at [`/index.html`](../index.html) rather
than under this directory; further examples go in `examples/<name>/`.

## [tic-tac-toe](../index.html)

**[Play it live →](https://uwussimo.github.io/ux-laws/)**

Tic-tac-toe is a useful test precisely because it is trivial. There is no feature work to hide
behind, so every difference between a careless version and a considered one is an interaction
decision. The default AI-built version is nine divs, an `alert("X wins!")`, and a reset button.

The prompt was three words. Everything below came from the skill, not the prompt.

What the skill changed:

| Law | Decision in the build |
| --- | --- |
| **Hick's** | Two opponents, both visible as a segmented control. No setup screen, no dropdown. |
| **Fitts's** | Cells are the largest thing on screen (min 88px, full-width grid); buttons are ~46px tall. |
| **Jakob's** | Standard 3×3 grid, X/O, arrow-key navigation that behaves like every other grid. |
| **Proximity** | Mode control, board, and score are three visibly separate groups. |
| **Miller's** | Score is three labelled numbers, not a sentence to parse. |
| **Doherty** | Your mark lands instantly; the computer answers in ~280ms — fast enough not to wait, slow enough to read as a move. |
| **Von Restorff** | Exactly one filled button ever exists, and only after the round ends. During play the board is the loud thing. |
| **Target distance** | Undo and New game sit directly under the board, inside the same card — not in a top toolbar. |
| **Serial position** | Whose turn it is comes first and largest; the next action comes last. |
| **Peak-End** | The ending names the winner *and* how they won ("Three in a row across the top row"), highlights the three cells, updates the score, and offers one obvious next action. |
| **Prägnanz** | One surface, one grid, no decorative gradients or dividers. |
| **Similarity** | X is always the same blue, O always the same red, in the board and the score. |
| **Uniform connectedness** | Status, board, and controls share a single card, so they read as one object. |
| **Tesler's** | The app tracks turns, win detection, score, and alternates who starts — the player tracks nothing. |
| **Postel's** | Tapping an occupied square shrugs (a nudge animation) instead of raising an error; Undo replaces "Are you sure?"; one undo rewinds the whole pair against the computer, because that is what "undo" means to the player. |
| **Parkinson's** | Playable on load. Zero taps of setup. |
| **Occam's** | Difficulty only appears when the opponent is the computer, because it is meaningless in 2-player mode. |
| **Pareto** | The 20% is tapping a cell and starting the next round; both are one tap, always in reach. |

Deliberate exception: the Zeigarnik effect has nothing to add here. A nine-square game needs no
progress meter, and adding one would violate Prägnanz to satisfy a checklist. The skill's own meta
rule applies — the laws are heuristics, not a scoring rubric.

---

## [chess](./chess/index.html)

**[Play it live →](https://uwussimo.github.io/ux-laws/examples/chess/)**

Chess is the opposite test from tic-tac-toe. The rules are genuinely complicated — pins, castling
rights, en passant, promotion, stalemate — so the question stops being "did you decorate the board"
and becomes "who carries the complexity, the player or the program?" Tesler's Law says the program,
and almost every decision below follows from that.

| Law | Decision in the build |
| --- | --- |
| **Tesler's** | The engine owns legality, check, mate, stalemate, notation, and material count. The player owns none of it. |
| **Postel's** | Illegal moves are unreachable rather than rejected — only legal destinations are offered, so there is no error state to design. Take-back replaces "are you sure?". |
| **Fitts's** | The board is the full width of the screen; squares land near 48px on a phone. |
| **Jakob's** | Tap-piece-then-square, dots for quiet moves, rings for captures — the pattern every chess app already uses. |
| **Hick's** | Two opponents, two difficulties, nothing else. Promotion offers four pieces with the queen leading, because it is the answer nearly every time. |
| **Occam's** | The promotion picker exists for the fraction of a second per game when it is relevant, and difficulty only when the opponent is a computer. |
| **Miller's** | Coordinates are printed on the board and the move list records the game, so nothing has to be held in memory. |
| **Doherty** | The engine answers in 10–79ms; the visible pause is a deliberate ~260ms, because a reply that lands instantly reads as a glitch. |
| **Von Restorff** | One filled button, only at the end. Check turns the status line red; the king's square turns red too, so it is never colour alone. |
| **Serial position** | Whose move it is is first and largest; the next action is last. |
| **Peak-End** | The ending names the result and the reason — "Checkmate on move 24", "Stalemate — no legal moves, but no check" — instead of a bare "Game over". |
| **Proximity / Uniform connectedness** | Status, board, and controls share one card; material and move list are separate groups below it. |
| **Prägnanz** | Two board colours, one highlight for the last move, one for check. No gradients, no piece shadows doing nothing. |
| **Pareto** | The 20% is: pick a piece, see where it goes, move it. That path is one tap deep and never blocked. |

Correctness is not a UX law, but an interface that allows an illegal move has no UX at all. The move
generator is verified with `perft` to depth 5 — 4,865,609 positions, matching the published count
exactly — plus targeted tests for castling through check, en passant, promotion, absolute pins,
back-rank mate, and stalemate.
