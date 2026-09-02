# UX Laws

[![skills.sh](https://skills.sh/b/uwussimo/ux-laws)](https://skills.sh/uwussimo/ux-laws)

**[Play the demo →](https://uwussimo.github.io/ux-laws/examples/tic-tac-toe/)** — tic-tac-toe, built with this skill loaded. [Source](./examples/tic-tac-toe/index.html) · [what changed, law by law](./examples/README.md)

Most AI-built interfaces suck.

Not because the models can't write React. They can. Not because they can't make something that looks polished. They can do that too.

The problem is that they optimize for *completion*, not *experience*.

Ask an agent to build a dashboard and you'll usually get a collection of buttons, cards, modals, dropdowns, tables, and sidebars that technically work. Everything is there. Nothing feels right.

A good interface is not a pile of components.

It is a sequence of decisions.

Where does my eye go first?  
What can I do next?  
What happens if I make a mistake?  
How much do I have to think?  
How far does my finger have to travel?  
Does this behave the way I already expect it to?

These are not aesthetic questions. They're interaction rules.

This skill is a collection of those rules.

The goal isn't to make AI-generated interfaces prettier. The goal is to make them feel like someone actually thought about the person using them.

---

## Installation

```bash
npx skills add uwussimo/ux-laws
```

That installs the skill into the current project. Other options:

```bash
npx skills add uwussimo/ux-laws -g                    # install globally, for every project
npx skills add uwussimo/ux-laws --agent claude-code   # install for one agent only
npx skills use uwussimo/ux-laws | claude              # try it without installing
```

The skill works with Claude Code, Cursor, Copilot, Windsurf, Gemini, Cline, and the other agents the
[`skills`](https://github.com/vercel-labs/skills) CLI supports. To install by hand instead, copy the
`ux-laws/` directory into your agent's skills directory (`~/.claude/skills/` for Claude Code).

Once installed, the skill activates on its own whenever you ask an agent to design, build, review, or
improve an interface — you don't need to mention it by name.

---

## The Laws

### 01. Hick's Law

> The more choices you give someone, the longer they take to choose.

Reduce choices per screen.

Don't expose every possible action just because the system supports it. Give the user the obvious next step and progressively reveal everything else.

**Do:**
- Keep primary actions obvious.
- Hide secondary actions behind menus.
- Reduce competing CTAs.
- Use progressive disclosure.

**Don't:**
- Put 7 buttons in a toolbar because "they might be useful."
- Give equal visual weight to actions with wildly different importance.

---

### 02. Fitts's Law

> Bigger, closer targets are easier to hit.

Make important interactive elements large enough to comfortably hit.

This matters even more on touch devices.

**Do:**
- Make primary buttons generous.
- Give touch targets enough spacing.
- Put frequent actions within easy reach.

**Don't:**
- Make users hunt for tiny icons.
- Put destructive actions directly beside common actions without protection.

---

### 03. Jakob's Law

> Users spend most of their time using other interfaces.

People already know how software works.

Don't invent new interaction patterns unless the benefit is worth the learning cost.

Use familiar:
- Navigation
- Search
- Forms
- Filters
- Menus
- Dialogs
- Gestures
- Keyboard shortcuts

Innovation should happen where it creates value—not where a standard pattern already works.

---

### 04. Law of Proximity

> Things that are close together are perceived as related.

Use spatial relationships to communicate hierarchy.

If a label describes an input, keep them close.

If two controls belong to the same task, group them.

Spacing is not decoration.

Spacing is information.

---

### 05. Miller's Law

> People can only keep a limited amount of information in working memory.

Don't make users remember things your interface could show them.

Break complex information into chunks.

**Do:**
- Group related fields.
- Break long processes into stages.
- Use sections and headings.
- Show contextual information where it is needed.

**Don't:**
- Force users to remember a value from three screens ago.
- Present giant walls of unrelated information.

---

### 06. Doherty Threshold

> Interfaces should respond quickly enough that the user feels the system is keeping up.

Aim for interactions to feel immediate.

A slow interface makes users question whether their action worked.

**Do:**
- Give immediate feedback.
- Use optimistic UI where appropriate.
- Show loading states for unavoidable delays.
- Preserve interaction continuity.

Never leave the user wondering:

> "Did that button actually do anything?"

---

### 07. Von Restorff Effect

> The thing that looks different gets noticed.

Use visual contrast to establish priority.

If everything is highlighted, nothing is highlighted.

There should usually be one obvious primary action.

**Do:**
- Give primary actions stronger visual weight.
- Use contrast intentionally.
- Make destructive actions visually distinct.

**Don't:**
- Make every button a primary button.
- Use bright colors everywhere.

---

### 08. Minimize Target Distance

Important actions should be close to the thing they're acting on.

Don't make users travel across the interface to complete an obvious local task.

For example:

Bad:

`Item → move mouse → sidebar → settings → action`

Better:

`Item → action`

Context should determine placement.

---

### 09. Serial Position Effect

> People tend to remember the beginning and end of a sequence better.

Put the most important information where users are most likely to notice it.

For navigation:
- Put important destinations first.
- Put frequently used actions in predictable locations.

For flows:
- Make the beginning obvious.
- Make the final action obvious.

---

### 10. Peak-End Rule

> People judge an experience largely by its peak moments and its ending.

The end of a flow matters disproportionately.

Don't finish an important task with:

> "Success."

Give users confidence.

Show:
- What happened.
- What changed.
- What they can do next.

A great completion state can make an otherwise ordinary workflow feel excellent.

---

### 11. Zeigarnik Effect

> People remember incomplete tasks better than completed ones.

Make progress visible.

If a task has multiple stages, tell the user where they are.

Examples:

`Step 2 of 4`

`██████░░░░ 60%`

`Profile → Payment → Confirmation`

Progress reduces uncertainty.

---

### 12. Law of Prägnanz

> People naturally perceive the simplest interpretation of a complex visual structure.

Simplify.

Don't make users understand your database schema through the UI.

Hide implementation complexity.

A complicated system can—and often should—have a simple interface.

---

### 13. Law of Similarity

> Things that look similar are perceived as related.

Consistency creates understanding.

Similar things should behave similarly.

Use consistent:
- Typography
- Icons
- Button styles
- Spacing
- States
- Interaction patterns

A user shouldn't have to relearn the interface on every screen.

---

### 14. Uniform Connectedness

> Visually connected elements are perceived as belonging together.

Use containers, borders, backgrounds, lines, and shared surfaces to communicate relationships.

More importantly:

Prevent errors before they happen.

If an action is unavailable, explain why.

If a field requires a specific format, show the format before submission.

Good UX doesn't merely explain mistakes.

It prevents them.

---

### 15. Tesler's Law

> Every system has some inherent complexity.

You cannot remove all complexity.

You can only decide who deals with it.

Make the system absorb complexity whenever possible.

Don't make the user understand:
- API limitations
- Database states
- Internal IDs
- Backend failures
- Implementation details

The product should carry its own complexity.

---

### 16. Postel's Law

> Be conservative in what you send, liberal in what you accept.

Interfaces should be forgiving.

Users will:
- Type spaces.
- Forget formatting.
- Paste unexpected values.
- Make small mistakes.
- Interpret instructions differently.

Accept reasonable input.

Normalize it when possible.

And when something genuinely cannot be accepted, explain exactly why.

---

### 17. Parkinson's Law

> Work expands to fill the time available for its completion.

Don't create unnecessary work.

If a task can take three steps, don't make it seven.

If the system already knows something, don't ask the user again.

If a default is obvious, provide it.

The fastest workflow is often the one that asks fewer questions.

---

### 18. Occam's Razor

> When multiple solutions work, prefer the simpler one.

Don't expose complexity prematurely.

Start simple.

Reveal advanced options only when they become relevant.

A good interface often has:

**Simple default → contextual detail → advanced control**

Not:

**Everything → everywhere → all the time**

---

### 19. Pareto Principle

> A small number of actions usually produce most of the value.

Find the 20% of actions users perform 80% of the time.

Optimize those first.

Make the common path:
- Faster
- More visible
- Easier
- More forgiving

Don't optimize obscure functionality before the main workflow feels effortless.

---

# The Meta Rule

These laws are not commandments.

They're heuristics.

A great interface sometimes violates them deliberately.

The important question isn't:

> "Does this follow UX Law #7?"

It's:

> "Does this make the user's job easier?"

---

# For AI Agents

When generating an interface, **do not start with components.**

Start with the user's task.

Before writing code, determine:

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

Then design the interface.

### The AI UI checklist

Before considering a screen complete, ask:

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

---

# The Standard

A technically correct interface is not necessarily a good interface.

A good interface makes the correct action feel obvious.

The user shouldn't have to think about the interface.

They should think about what they're trying to accomplish.

**Build the interface around the user's intention, not the application's architecture.**
