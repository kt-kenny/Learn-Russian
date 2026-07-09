# Learn Russian

Grammar-first Russian course (target: A2) as an MkDocs site, with a built-in spaced-repetition flashcard app.

## Publish to GitHub Pages

```bash
cd "~/Claude/Projects/Learn Russian"
git init -b main
git add -A
git commit -m "Russian learning site + flashcard app"
gh repo create learn-russian --public --source=. --push
# or: create the repo on github.com, then:
# git remote add origin git@github.com:YOURNAME/learn-russian.git && git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: GitHub Actions**. The included workflow (`.github/workflows/deploy.yml`) builds and deploys on every push. Site appears at `https://YOURNAME.github.io/learn-russian/`.

## Run locally

```bash
pip install -r requirements.txt
mkdocs serve   # http://127.0.0.1:8000
```

The flashcard app also works standalone — just open `docs/flashcards/index.html` in a browser. Progress is stored in your browser's localStorage.

## Layout

- `PLAN.md` — project breakdown
- `docs/roadmap.md` — the 6-month study plan; start there
- `docs/grammar/` — 13 lessons in dependency order
- `docs/phrases/` — Cyrillic / literal gloss / natural English
- `docs/practice/` — drills with hidden answer keys
- `docs/flashcards/` — the app (9 decks, 270 cards)
