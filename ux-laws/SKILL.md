---
name: ux-laws
description: Apply the 19 UX laws (Hick's, Fitts's, Jakob's, Proximity, Miller's, Doherty threshold, Von Restorff, target distance, Serial Position, Peak-End, Zeigarnik, Prägnanz, Similarity, Uniform Connectedness, Tesler's, Postel's, Parkinson's, Occam's razor, Pareto) while designing, building, or reviewing any user interface or user flow. Use this whenever the user asks to design or build a screen, page, component, form, dashboard, onboarding, checkout, settings panel, wearable or mobile UI, or app in HTML, React, SwiftUI, Flutter, or any framework; whenever they ask to critique, audit, or improve a mockup, screenshot, wireframe, or existing UI; whenever they mention usability, conversion, friction, "easier to use", "cleaner", "less confusing", or "why do users drop off" — even if they never say "UX law" or "heuristic". Also use it when asked to explain a UX law or run a heuristic review.
---

# UX Laws

Most AI-built interfaces technically work and still feel wrong. Not because the model can't write React or make something polished — it can. The problem is that it optimizes for *completion*, not *experience*: a collection of buttons, cards, modals, and tables where everything is present and nothing feels right.

A good interface is not a pile of components. It is a sequence of decisions:

- Where does my eye go first?
- What can I do next?
- What happens if I make a mistake?
- How much do I have to think?
- How far does my finger have to travel?
- Does this behave the way I already expect it to?

These are interaction rules, not aesthetic preferences. This skill is the collection of those rules. The goal is not prettier output; it is output that feels like someone thought about the person using it.

## Start with the task, not the components

Before writing any UI code or drawing any screen, answer:

1. What is the user's primary goal?
2. What is the most common action?
3. What information does the user need immediately?
4. What decisions can be removed?
5. What complexity can the system absorb?
6. What can go wrong?
7. How does the user recover?
8. What should happen immediately after each action?
9. What should be visually dominant?
10. What should be hidden until needed?

Then design. The answers decide layout, hierarchy, defaults, and error handling before a single component is chosen.

## How to use the laws

**Building** (wireframes, HTML/React/SwiftUI/Flutter, artifacts, dashboards, forms, flows): answer the ten questions, design, then run the checklist near the end of this file before calling anything done. Fix what fails quietly — the user wants a better screen, not a bibliography. Name a law only when it explains a non-obvious choice.

**Reviewing** (screenshot, mockup, wireframe, Figma export, existing code): walk the laws, record only real findings, rank by impact, and use the audit format below. Lead with the fix, then cite the law once so the user can look it up.

**Explaining / teaching**: read `references/laws.md` for origins, what the research actually claims, and common misreadings. Answer at the depth asked.

## The laws

### 01. Hick's Law — reduce choices per screen
> The more choices you give someone, the longer they take to choose.

Don't expose every action just because the system supports it. Give the obvious next step and progressively reveal the rest.
- **Do:** keep primary actions obvious; hide secondary actions behind menus; reduce competing CTAs; recommend a default when one fits most people.
- **Don't:** put seven buttons in a toolbar because they "might be useful"; give equal visual weight to actions of wildly different importance.
- *Smell:* forty toggles on one settings screen.

### 02. Fitts's Law — make targets large
> Bigger, closer targets are easier to hit.

Make important interactive elements large enough to hit comfortably. This matters even more on touch devices.
- **Do:** generous primary buttons (at least ~44×44 pt on touch, ~24×24 px plus spacing on desktop); space between adjacent targets; hit areas padded beyond the visible shape; frequent actions within easy reach — the bottom third of a phone screen.
- **Don't:** make users hunt for tiny icons; put destructive actions directly beside common ones without protection.
- *Smell:* "Next" in the top-right corner of a mobile form.

### 03. Jakob's Law — follow familiar patterns
> Users spend most of their time using other interfaces.

People already know how software works. Don't invent new interaction patterns unless the benefit is worth the learning cost.
- **Use familiar:** navigation, search, forms, filters, menus, dialogs, gestures, keyboard shortcuts.
- Innovate where it creates value, not where a standard pattern already works. When you change something familiar, ease the transition.
- *Smell:* a custom gesture nobody discovers; an icon that means something else everywhere else.

### 04. Law of Proximity — group related information
> Things that are close together are perceived as related.

Spacing is not decoration. Spacing is information.
- If a label describes an input, keep them close. If two controls belong to the same task, group them.
- Put whitespace *between* groups, not between members — grouping comes from the contrast in spacing.
- *Smell:* uniform spacing everywhere, so nothing reads as a group.

### 05. Miller's Law — break content into chunks
> People can only keep a limited amount of information in working memory.

Don't make users remember things the interface could show them.
- **Do:** group related fields; break long processes into stages; use sections and headings; show contextual information where it's needed; format long strings the way people already chunk them (4-4-4-4 card numbers).
- **Don't:** force users to remember a value from three screens ago; present walls of unrelated information.
- *Smell:* an unbroken 16-digit input.

### 06. Doherty Threshold — respond within 400 ms
> The interface should respond quickly enough that the user feels the system is keeping up.

A slow interface makes users question whether their action worked. Never leave them wondering, "Did that button do anything?"
- **Do:** give immediate feedback; use optimistic UI where appropriate; show loading states (skeletons, progress) for unavoidable delays; preserve interaction continuity.
- Cut real latency first; when you can't, make *something* visible within 400 ms.
- *Smell:* a tap that shows nothing for a second.

### 07. Von Restorff Effect — highlight the primary action
> The thing that looks different gets noticed.

If everything is highlighted, nothing is highlighted. There should usually be one obvious primary action per screen.
- **Do:** give primary actions stronger visual weight; use contrast intentionally; make destructive actions visually distinct (not by color alone).
- **Don't:** make every button a primary button; use bright colors everywhere.
- *Smell:* two filled buttons side by side.

### 08. Minimize Target Distance — place key actions nearby
Important actions belong close to the thing they act on (the other half of Fitts's Law). Don't make users travel across the interface to complete an obvious local task.
- Bad: `Item → sidebar → settings → action`. Better: `Item → action`.
- Context determines placement: submit below the form, edit beside the field, confirm next to the trigger.
- *Smell:* a row-level action that lives only in a global toolbar.

### 09. Serial Position Effect — put essentials first
> People remember the beginning and end of a sequence better.

Put the most important information where users are most likely to notice and recall it.
- **Navigation:** important destinations first; frequently used actions in predictable locations; the least important in the middle.
- **Flows:** make the beginning obvious and the final action obvious.
- *Smell:* Home in position 4 of 6.

### 10. Peak-End Rule — end flows memorably
> People judge an experience largely by its peak moments and its ending.

Don't finish an important task with "Success." Give users confidence: show what happened, what changed, and what they can do next. A great completion state makes an ordinary workflow feel excellent.
- The peak can be negative: find the worst moment in the flow (payment failure, denied permission) and soften it.
- *Smell:* a flow that ends on a blank page or a raw confirmation string.

### 11. Zeigarnik Effect — show visible progress
> People remember incomplete tasks better than completed ones.

If a task has multiple stages, tell the user where they are. Progress reduces uncertainty.
- Examples: `Step 2 of 4` · `██████░░░░ 60%` · `Profile → Payment → Confirmation`
- Related — **Goal-Gradient Effect:** effort rises as the goal nears, so make completion feel closer: start progress at an honest non-zero value (signing up counts), show remaining steps shrinking, make the last step the lightest.
- *Smell:* a multi-step flow with no sense of position.

### 12. Law of Prägnanz — simplify complex interfaces
> People perceive the simplest interpretation of a complex visual structure.

Simplify. Don't make users understand your database schema through the UI. A complicated system can — and usually should — have a simple interface.
- Use clear shapes, an aligned grid, and an obvious hierarchy; when a screen feels busy, remove visual noise before adding explanation.
- *Smell:* dividers, gradients, and icons that carry no meaning.

### 13. Law of Similarity — maintain pattern consistency
> Things that look similar are perceived as related.

Consistency creates understanding. Similar things should behave similarly, and the user shouldn't relearn the interface on every screen.
- **Keep consistent:** typography, icons, button styles, spacing, states, interaction patterns.
- The sharp edge is the converse: anything that *looks* alike but behaves differently is a bug.
- *Smell:* three shades of "primary" blue; a heading styled like a button.

### 14. Uniform Connectedness — connect related elements visually
> Visually connected elements are perceived as belonging together.

Use containers, borders, backgrounds, lines, and shared surfaces to communicate relationships. Connection reads more strongly than proximity or similarity alone, so reserve it for the relationships that must not be missed.
- Wrap a form section in a card; join wizard steps with a line; put an input and its button in one container.
- *Smell:* boxes inside boxes; a Save button floating far from the fields it saves.

### 15. Tesler's Law — use sensible defaults
> Every system has some inherent complexity.

You cannot remove all complexity. You can only decide who deals with it. Make the system absorb it whenever possible: smart defaults, auto-detect, remembered input, inferred formats, auto-save.
- **Don't make the user understand:** API limitations, database states, internal IDs, backend failures, implementation details.
- *Smell:* a time-zone dropdown instead of auto-detect with an override.

### 16. Postel's Law — prevent errors, and make them recoverable
> Be conservative in what you send, liberal in what you accept.

Interfaces should be forgiving. Users type spaces, forget formatting, paste unexpected values, make small mistakes, and interpret instructions differently. Accept reasonable input and normalize it.
- **Prevent errors before they happen:** show the required format before submission; validate inline; if an action is unavailable, explain why; constrain with pickers and masks where the intent is unambiguous.
- **Make errors recoverable:** keep everything the user typed; say exactly what's wrong and how to fix it, next to the problem; offer undo instead of "Are you sure?"; never dead-end.
- *Smell:* "Invalid input"; a form that clears itself on error.

### 17. Parkinson's Law — reduce task completion time
> Work expands to fill the time available for its completion.

Don't create unnecessary work. If a task can take three steps, don't make it seven. If the system already knows something, don't ask again. If a default is obvious, provide it.
- Set an honest expectation ("about 2 minutes"), then beat it. The fastest workflow is usually the one that asks fewer questions.
- *Smell:* a checkout asking for information you could derive or postpone.

### 18. Occam's Razor — reveal complexity gradually
> When multiple solutions work, prefer the simpler one.

Don't expose complexity prematurely. Start simple and reveal advanced options only when they become relevant.
- **Simple default → contextual detail → advanced control**, not **everything → everywhere → all the time**.
- Remove any element whose absence wouldn't hurt the task; hide (don't delete) the rest.
- *Smell:* every option visible at once "just in case".

### 19. Pareto Principle — optimize the common path first
> A small number of actions usually produce most of the value.

Find the 20% of actions users perform 80% of the time and optimize those first: faster, more visible, easier, more forgiving.
- Don't polish obscure functionality before the main workflow feels effortless.
- *Smell:* the most-used action three taps deep while a rare one sits on the home screen.

## When laws collide

- **Hick's (fewer choices) vs. Tesler's (someone carries the complexity):** hide options, don't remove them — a default plus an override satisfies both.
- **Von Restorff (one thing stands out) vs. Similarity (same look, same function):** exactly one primary action per screen; everything else consistent and quiet.
- **Jakob's (familiar) vs. Occam's (minimal):** familiar wins for navigation and forms; minimal wins for content and decoration.
- **Speed (Doherty, Parkinson) vs. visible progress (Zeigarnik):** make it fast; if it can't be fast, make it visibly progressing.
- **Miller's (chunk) vs. Hick's (fewer):** chunking isn't adding — five groups of three beats fifteen flat items, and both beat hiding what people need.

## The checklist — before considering a screen complete

- [ ] Is there one obvious primary action?
- [ ] Are secondary actions visually subordinate?
- [ ] Are related elements grouped?
- [ ] Is the common path short?
- [ ] Are targets large enough?
- [ ] Does the UI use familiar patterns?
- [ ] Is important information visible without memorization?
- [ ] Is progress visible for multi-step tasks?
- [ ] Are loading states immediate and informative?
- [ ] Are errors prevented where possible?
- [ ] Can users recover from errors?
- [ ] Are defaults sensible?
- [ ] Is complexity revealed progressively?
- [ ] Is the interface consistent across screens?
- [ ] Does the completion state clearly communicate success?
- [ ] Can the user understand what to do next without thinking?

## Audit format — for reviews

Keep it short and ranked; the user wants the top fixes, not nineteen paragraphs.

```
**Top fixes**
1. [Finding] → [concrete fix]. (Law)
2. ...
3. ...

**Works well**
- [1–3 things to keep, with the law they satisfy]

**Quick check**
Cognitive load · Targets & speed · Attention · Memory & motivation · Error tolerance
— one line each: ✅ or ⚠️ plus a short note
```

Skip laws that can't apply to the artifact (Doherty Threshold on a static mockup, Peak-End on a single component). Three excellent findings beat fifteen mediocre ones.

## The meta rule

These laws are heuristics, not commandments. A great interface sometimes violates one deliberately. The question is never "does this follow law #7?" — it is "does this make the user's job easier?"

A technically correct interface is not necessarily a good one. A good interface makes the correct action feel obvious, so the user thinks about what they're trying to accomplish instead of about the interface. **Build the interface around the user's intention, not the application's architecture.**

## Reference

`references/laws.md` — one entry per law: origin, what the research actually claims, common misreadings, and extra examples. Read it when explaining a law, when a user quotes a law with an unexpected takeaway (popular summaries often shuffle the labels), or when a finding needs backing.
