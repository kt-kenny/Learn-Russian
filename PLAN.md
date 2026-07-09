# Project Plan — Learn Russian

Two deliverables, built into one MkDocs site deployable on GitHub Pages.

## Learner profile

- ~6 months Duolingo: decent recognition vocabulary, can sound out Cyrillic slowly
- Weak grammar (Duolingo's known gap) → grammar is the priority
- Target: **A2 in ~6 months**

## Deliverable 1 — Learning site (MkDocs)

```
docs/
  index.md              How to use this site
  roadmap.md            6-month week-by-week plan
  alphabet.md           Reading fluency + pronunciation rules
  grammar/              13 lessons, ordered by dependency (cases first)
  phrases/              6 themed phrase sets: Cyrillic / literal gloss / natural English
  practice/             Drills with hidden answer keys
  flashcards/           The webapp (Deliverable 2), served as static files
  resources.md          Input sources, media, next steps
```

Grammar ordering rationale: gender/nouns → accusative (easiest case) → prepositional →
genitive → dative → instrumental → present tense → past/future → **aspect** (the hard one) →
adjectives → pronouns → numbers/time → verbs of motion (intro only at A2).

Phrase format convention (used everywhere):

> **Как дела?** — lit. *"How affairs?"* — "How's it going?"

## Deliverable 2 — Flashcard webapp

- Single-page static HTML/JS/CSS (no build step) at `docs/flashcards/index.html`
- Decks in `docs/flashcards/decks/*.json` — phrases decks + grammar decks (case endings, conjugations, aspect pairs)
- SM-2-style spaced repetition, progress in `localStorage`
- Card front: Russian (or English prompt for production practice); back: literal gloss + natural meaning + notes
- Works offline once loaded; deployable on the same GitHub Pages site

Deck JSON schema:

```json
{ "name": "...", "description": "...",
  "cards": [{ "front": "...", "back": "...", "literal": "...", "notes": "..." }] }
```

## Execution (subagents, Sonnet)

| Agent | Scope |
|---|---|
| A | `alphabet.md` + all `grammar/*.md` |
| B | all `phrases/*.md` + all `practice/*.md` + `resources.md` |
| C | flashcard app + decks |

Then: `mkdocs build` verification, content spot-check, git push instructions.
