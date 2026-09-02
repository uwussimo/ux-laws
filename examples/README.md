# Examples

Interfaces built with the `ux-laws` skill loaded, kept here so the laws can be read against real
output instead of in the abstract.

Each example is a single self-contained HTML file — open it directly in a browser, no build step.

## [tic-tac-toe](./tic-tac-toe/index.html)

**[Play it live →](https://uwussimo.github.io/ux-laws/examples/tic-tac-toe/)**

Tic-tac-toe is a useful test precisely because it is trivial. There is no feature work to hide
behind, so every difference between a careless version and a considered one is an interaction
decision. The default AI-built version is nine divs, an `alert("X wins!")`, and a reset button.

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
