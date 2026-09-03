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
| **Fitts's (desktop)** | A phone layout centred in a 1900px window wastes the screen and shrinks the targets. Above 900px the board takes a 600px column and the record of the game — material, moves, review — moves into a sidebar beside it, so nothing falls below the fold and the squares get ~50% larger. Pieces are sized in container-query units, so they stay the same fraction of a square at every board size. |
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
| **Similarity / Prägnanz** | The board is exempt from the theme. Dark mode originally recoloured the squares, which put black pieces at 1.29:1 against them — the pattern survived, the pieces didn't. Classic square colours now hold in both themes; only the chrome around the board changes. |
| **Peak-End (the review)** | The game ends into a lesson, not a dead end. At game over the review — not "Play again" — is the one filled button, because after a loss the useful next step is understanding it; once you've used it, Play again takes the highlight back. |
| **Sound** | Eight sounds, each answering a question the screen answers slower. A capture is heavier and darker than a quiet move; check is the one sound that is unmistakably not a move; take-back reverses rather than advances. Synthesised with WebAudio, so the file stays self-contained — no assets. |

### The post-game review

Every move you played is re-searched, and the loss is measured in win-probability points rather than
centipawns — losing 200 centipawns matters enormously at level and not at all when already winning.
That produces an accuracy score, a grade per move, and the three moments that actually decided the
game, worst first.

Three decisions did most of the work:

- **The board is the explanation.** Tapping a moment puts that position back on the board with the
  move you played in red and the engine's choice in green. A sentence about move 24 teaches far less
  than move 24 on the board in front of you.
- **Claims are concrete or absent.** The review only says things the engine can demonstrate — "it
  leaves your knight on f6 undefended — Nxf6 takes it", "there was a free rook on a8", "it allows
  mate: Qh4#". Where it cannot explain, it reports the size of the mistake and stops. Vague
  evaluation talk would sound authoritative and teach nothing.
- **Advice has to be playable.** At this depth many moves tie, and the search originally returned the
  first one in generation order — producing "a4 was better", which is true and useless. Ties now
  break toward captures, central squares, and developing moves, so the same position advises "Nc3".

### The guided walkthrough

After the review, the game can replay itself: each move slides across the board, and at every mistake
it stops, marks the board, and explains what went wrong — spoken aloud through the browser's own
speech synthesis.

- **Nothing is audio-only.** Every spoken sentence is printed as a caption at the same moment. The
  walkthrough is identical with the voice off, on a muted phone, in a browser with no speech support,
  or for someone who cannot hear it — the voice is an enhancement of the caption, never a replacement.
- **Pacing follows whichever channel is carrying it.** With a voice, each step waits for the sentence
  to finish. Without one, captions hold long enough to read — the first version flashed the opening
  line past in under 20ms, which the tests caught.
- **Notation becomes speech.** `Bxc6` is read "Bishop takes C 6", `O-O` as "castles kingside",
  `gxh8=Q+` as "G takes H 8, promoting to queen, check". Reading raw notation aloud teaches nobody.
- **Ordinary moves don't interrupt.** Only mistakes stop the replay and speak; the rest flow past at
  reading speed. Narrating all fifty moves would be thorough and unbearable.
- **The animation is the point, not decoration.** A piece that travels shows you which piece moved and
  how far; a piece that teleports makes you diff two positions. It honours `prefers-reduced-motion`.

The headline lesson is derived from the pattern in the mistakes (pieces left hanging, captures walked
past, a mate allowed), not chosen from a list of platitudes. And the panel states plainly what the
engine is: depth 3, reliable on hung pieces, missed captures and mates, not a substitute for a real
engine on quiet positional moves. A teaching tool that overstates its own authority teaches the wrong
lesson twice.

Sound follows the same rule as everything else here: it has to carry information. Picking a piece
up speaks and putting it down doesn't, because only one of those is a commitment. The computer's
reply is audible so you can look away and still know it moved. The mute switch is one control rather
than a mixer (Hick's), it remembers itself across visits (Tesler's), it survives a browser with no
audio or no storage without taking the game down (Postel's), and no `AudioContext` is ever created
while muted.

Contrast is measured rather than eyeballed. Every piece/square pair clears 4.5:1 — white pieces
carry their contrast in a `-webkit-text-stroke` edge (10.8:1) since white-on-cream fill is only
1.37:1 — and the legal-move dots were opened from 32% to 60% opacity after measuring 1.77:1 against
the dark squares. The one deliberate exception is the board pattern itself at 2.29:1: that is what a
chess board has always looked like, and pushing the two square colours apart to satisfy a number
would make the pieces harder to read, not easier. The meta rule wins over the checklist.

Correctness is not a UX law, but an interface that allows an illegal move has no UX at all. The move
generator is verified with `perft` to depth 5 — 4,865,609 positions, matching the published count
exactly — plus targeted tests for castling through check, en passant, promotion, absolute pins,
back-rank mate, and stalemate.
