# UX Laws — reference

One entry per law: where it comes from, what it actually claims, how it gets misread, and examples beyond the ones in SKILL.md. Load this when explaining a law, defending a finding, or untangling a mislabeled summary.

Contents: A. Cognitive load · B. Targets & speed · C. Attention & perception · D. Memory, motivation, emotion · E. Error tolerance · Label mix-ups · Sources

---

## A. Cognitive load

### Hick's Law
- **Origin:** William Hick (1952) and Ray Hyman (1953); often "Hick–Hyman law." Choice reaction time rises roughly with the logarithm of the number of equally likely options.
- **Claim:** More (and more complex) options → slower decisions. Logarithmic, not linear: going from 2 to 4 options hurts more than from 40 to 42.
- **Misreadings:** It is not "always show fewer things." Removing options users need shifts the cost to search and memory. It also assumes unordered options — a well-ordered list (alphabetical, grouped) can be scanned faster than the law predicts.
- **Examples:** A remote with 6 buttons vs. 60. A pricing page with 3 plans and one marked "Most popular." A command palette that filters as you type (search beats choice).

### Miller's Law
- **Origin:** George A. Miller, 1956, "The Magical Number Seven, Plus or Minus Two."
- **Claim:** Short-term memory holds a limited number of *chunks*; chunking lets you hold more information in the same slots.
- **Misreadings:** "Max 7 menu items" is a folk rule Miller never made — menus are perceived, not memorized, so the cap doesn't apply. Later work (Cowan, 2001) puts the real span nearer 4 chunks. Use the law to justify chunking and formatting, not to cap navigation.
- **Examples:** 4-4-4-4 card numbers; grouped settings; a confirmation code shown as 3 + 3 digits.

### Law of Prägnanz
- **Origin:** Gestalt psychology (Wertheimer, Koffka, 1920s). *Prägnanz* ≈ "conciseness" or "good form."
- **Claim:** Perception resolves ambiguity toward the simplest, most regular, stable interpretation. Complexity costs effort before any thinking begins.
- **Misreadings:** It is about *perceptual* simplicity — alignment, regular shapes, clear figure/ground — not about removing features (that's Occam's razor and Tesler's law).
- **Examples:** Icons built on a shared grid read faster than a mixed set. A dashboard with four aligned cards vs. a collage of widget sizes.

### Occam's Razor
- **Origin:** William of Ockham, 14th-century friar and philosopher: don't multiply entities beyond necessity.
- **Claim (design reading):** Among designs that perform equally, prefer the one with the fewest elements and assumptions.
- **Misreadings:** "Fewest elements" is not "fewest features." Cutting a needed feature isn't simplicity; hiding it behind progressive disclosure often is. Test each element by asking what breaks if it disappears.
- **Examples:** A search box that hides filters until you type. An export dialog with one recommended format and an "Other formats" expander.

### Tesler's Law (law of conservation of complexity)
- **Origin:** Larry Tesler, Xerox PARC and Apple, mid-1980s.
- **Claim:** Every application has an irreducible amount of complexity. It can be moved between the system (engineers) and the user, but not removed.
- **Misreadings:** It's not an excuse for complex UIs ("it's inherent"). Most complexity in a UI is *not* inherent; the law applies to what remains after honest simplification, and says the system should absorb it.
- **Examples:** Address autocomplete instead of five fields. A mail client that guesses the recipient from a partial name. Currency inferred from location, editable later.

### Pareto Principle
- **Origin:** Vilfredo Pareto (1896) observed 80% of Italian land held by 20% of people; Joseph Juran generalized it as the "vital few."
- **Claim:** Outcomes are unevenly distributed; a minority of causes drive most effects. In products, a few features carry most usage and value.
- **Misreadings:** The numbers aren't literally 80/20. The lesson is prioritization: measure which flows matter, then spend disproportionate design effort there. It does not say "delete the other 80% of features."
- **Examples:** Optimizing the compose flow in a messaging app before the profile editor. Putting the three most-used actions in a tab bar and the rest in a menu.

---

## B. Targets & speed

### Fitts's Law
- **Origin:** Paul Fitts, 1954. Movement time = a + b · log₂(2D/W) — grows with distance D, shrinks with target width W.
- **Claim:** Bigger and nearer targets are faster to acquire. On touch screens, size dominates; for cursors, screen edges and corners act as infinitely deep targets.
- **Misreadings:** Applies to *pointing*, not to everything. Also, huge targets have diminishing returns and steal space. Apple recommends ≥44×44 pt, Material ≥48×48 dp, WCAG 2.2 sets 24×24 CSS px as the minimum.
- **Examples:** Full-width primary buttons at the bottom of mobile forms. Menu bars pinned to the screen edge. Padding the tappable area around a small icon.

### Doherty Threshold
- **Origin:** Walter Doherty and Ahrvind Thadani, IBM, 1982, on the economic value of rapid response time.
- **Claim:** When system response stays under ~400 ms, users stay in flow and productivity rises disproportionately.
- **Misreadings:** Perceived speed counts. Skeleton screens, optimistic UI, and instant acknowledgment ("Sending…") keep the conversation going even when the real work takes longer. Conversely, a *too-fast* response for a heavy action (e.g., a "security scan" finishing in 30 ms) can feel untrustworthy — occasionally a brief, honest progress state helps.
- **Examples:** Liking a post updates instantly and syncs later. Search that shows results as you type.

### Parkinson's Law
- **Origin:** C. Northcote Parkinson, 1955 essay in *The Economist*, on bureaucratic growth.
- **Claim:** Work expands to fill the time available. In UX: if a task has no felt time pressure or expectation, users (and flows) sprawl.
- **Misreadings:** Not a license for countdown timers and dark-pattern urgency. The design move is to set an honest expectation and then remove steps so the flow beats it.
- **Examples:** "Sign-up takes 30 seconds" above a two-field form. Autofilled shipping from a saved profile. Guest checkout.

---

## C. Attention & perception (Gestalt)

### Law of Proximity
- **Origin:** Gestalt grouping principle (Wertheimer, 1923).
- **Claim:** Elements near each other are perceived as a group.
- **Misreadings:** Consistent spacing is not the same as *meaningful* spacing. If every gap is 16 px, proximity carries no information; grouping comes from the *contrast* between intra-group and inter-group space.
- **Examples:** Label 4 px above its field, 24 px below the previous field. Related settings clustered under a heading with generous space between clusters.

### Law of Similarity
- **Origin:** Gestalt grouping principle.
- **Claim:** Elements sharing color, shape, size, or texture are perceived as related and expected to behave alike.
- **Misreadings:** It's often summarized as "consistency," which is right, but the sharp edge is the converse: anything that *looks* similar but behaves differently is a bug. Underlined blue text must be a link; identical cards must open the same way.
- **Examples:** One button style per action type across the whole app. Status chips with a stable color mapping.

### Law of Uniform Connectedness
- **Origin:** Stephen Palmer and Irvin Rock, 1994 — a later addition to the Gestalt principles.
- **Claim:** Elements connected by a visible line, border, or common region are perceived as more related than elements that are merely near or similar. Connectedness usually overrides proximity and similarity.
- **Misreadings:** Overuse produces boxes inside boxes. Reserve strong connection (borders, backgrounds) for the relationships that must not be missed.
- **Examples:** A card containing a preview and its actions. Wizard steps joined by a line. A sparkline drawn through its data points.

### Von Restorff Effect (isolation effect)
- **Origin:** Hedwig von Restorff, 1933.
- **Claim:** In a set of similar items, the one that differs is most likely to be noticed and remembered.
- **Misreadings:** Highlighting works only against a quiet background. Every additional "highlight" halves the effect of the others. Also, don't rely on color alone — it fails for color-blind users; pair it with shape, weight, or position.
- **Examples:** One filled CTA, secondary actions as text buttons. A red destructive action separated from the rest of a menu.

### Jakob's Law
- **Origin:** Jakob Nielsen, 2000.
- **Claim:** Users spend most of their time on *other* products, so they expect yours to work the same way.
- **Misreadings:** It is not "never innovate." It says convention is the default and novelty has to earn its cost. When you change a familiar pattern, let users keep the old one for a while or teach the new one in place.
- **Examples:** Cart icon top-right. Pull-to-refresh. Settings under a gear. Form fields stacked, labels above.

---

## D. Memory, motivation, emotion

### Serial Position Effect
- **Origin:** Hermann Ebbinghaus, 1885 (primacy and recency effects).
- **Claim:** Items at the beginning and end of a sequence are recalled best; middle items are recalled worst.
- **Misreadings:** It concerns *recall*, so it matters most where users must remember something: nav order, onboarding messages, lists of options they'll choose from later. For scanning within a visible list, position matters less than grouping.
- **Examples:** Home first and Profile last in a tab bar, low-priority items in the middle. Key takeaway stated at the start and repeated at the end of a tutorial.

### Zeigarnik Effect
- **Origin:** Bluma Zeigarnik, 1927, noting that waiters remembered unpaid orders better than paid ones.
- **Claim:** Uncompleted or interrupted tasks are remembered better and create a pull to finish.
- **Misreadings:** The original finding replicates inconsistently; treat it as a design heuristic, not settled science. And don't weaponize it — artificial incompleteness (fake "3 unfinished items") erodes trust fast.
- **Examples:** Progress rings on a profile. "Continue where you left off" cards. Checklists in onboarding.

### Goal-Gradient Effect
- **Origin:** Clark Hull, 1932 (animals run faster as they near a reward); Kivetz, Urminsky & Zheng, 2006 (coffee loyalty cards pre-stamped twice were completed faster than blank ones with the same remaining effort).
- **Claim:** Motivation and effort increase as the goal gets closer; perceived proximity matters as much as real proximity.
- **Misreadings:** "Start at 20%" is honest only if the user actually did something (signing up counts). Padding progress that isn't real is deception and, once noticed, backfires. Also, motivation drops right after a goal is reached — plan the next goal.
- **Examples:** "2 of 5 steps done" immediately after account creation. Shrinking "3 items left" copy. A lighter final step.

### Peak-End Rule
- **Origin:** Daniel Kahneman, Barbara Fredrickson and colleagues, 1990s (cold-water and medical-procedure studies).
- **Claim:** People judge an experience by its most intense moment and its end, largely ignoring duration and average.
- **Misreadings:** The peak can be negative. Fixing the worst moment (a confusing error, a permission prompt at the wrong time) often improves the remembered experience more than adding delight. Endings include *unhappy* endings — how a cancellation or refund flow ends shapes what people say about you.
- **Examples:** Order confirmation with a clear "what happens next." A friendly, specific payment-failure message. Empty states that celebrate a cleared inbox.

---

## E. Error tolerance

### Postel's Law (robustness principle)
- **Origin:** Jon Postel, 1980–81, TCP specification: be conservative in what you send, liberal in what you accept.
- **Claim (design reading):** Anticipate the full range of what users might do or enter, accept as much of it as you reasonably can, and respond with clear, predictable output.
- **Misreadings:** "Accept anything" doesn't mean "never validate." Normalize input silently where the intent is unambiguous (spaces in a card number), and ask only when it's not (an ambiguous date). Also covers *access*: assistive tech, slow networks, odd viewports.
- **Examples:** Phone fields that accept any spacing or punctuation. Dates typed as "tomorrow." Undo toasts instead of confirm dialogs. Errors that keep the user's data and point to the exact field.

---

## Label mix-ups you may see in summaries

Popular videos, listicles, and some versions of this very skill pair a law with the wrong takeaway. When a user quotes one of these, apply the principle they clearly mean and, if useful, note the standard name once.

| Summary says | Standard law for that takeaway |
|---|---|
| "Uniform connectedness: prevent errors before they happen" | Postel's Law and general error tolerance (kept under #16 in SKILL.md) |
| "Law of similarity: use sensible defaults" | Tesler's Law (system absorbs complexity) |
| "Tesler's law: make errors recoverable" | Postel's Law |
| "Postel's law: maintain pattern consistency" | Law of Similarity (and Jakob's Law) |
| "Postel's law: connect elements visually" | Law of Uniform Connectedness |
| "Pareto principle: make completion feel closer" | Goal-Gradient Effect (noted under #11 Zeigarnik in SKILL.md) |
| "Occam's razor: reveal complexity gradually" | Progressive disclosure, a tactic serving Occam's razor and Tesler's Law |
| "Minimize target distance" (as its own law) | Second half of Fitts's Law — kept as #08 because the source skill numbers it that way |

## Sources

Jon Yablonski, *Laws of UX* (lawsofux.com and the O'Reilly book) is the usual collection these lists are drawn from. Primary sources are named in each entry above; the specific numbers (400 ms, 44 pt, 7 ± 2) come from Doherty & Thadani (1982), Apple's Human Interface Guidelines, and Miller (1956) respectively.
