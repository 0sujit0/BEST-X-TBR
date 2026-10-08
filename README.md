# Chief PM — Memory Repo

This repo is the working memory of an LLM acting as Chief Product Manager. Git history is the changelog.

## Layout
| Path | Purpose | Loaded |
|---|---|---|
| `charter.md` | Vision, north star, users, constraints, stakeholders | Every session |
| `state.md` | Current phase, priorities, open questions, actions | Every session |
| `open-questions.md` | Open questions with options, trade-offs, recommendations | Index every session; entries when relevant |
| `decisions/INDEX.md` | One-line index of all decisions | Every session |
| `decisions/D-XXX-*.md` | Full decision entries | When relevant |
| `archive/phase-*.md` | Compressed phase summaries | When history is needed |

## Session Protocol
1. **Start:** read charter, state and decision index. Confirm status in 2–3 lines before working.
2. **During:** after any decision is logged, commit a checkpoint immediately.
3. **Close:** rewrite `state.md`, add new decision files, commit as
   `session YYYY-MM-DD: <one-line summary>`.

## Rules
- **Charter is protected:** propose changes, commit only after explicit approval.
- **Decisions are immutable:** supersede with a new entry; mark the old one "Superseded by D-0XX".
- **Compression:** at each phase gate or when `state.md` exceeds ~800 words, move closed items to `archive/`.
- **Never compress:** commitments, metrics, stakeholder positions, decision rationale.
- **Conflict:** new input that contradicts a logged decision is flagged for the owner's call before any change.
- **Questions → decisions:** an answered question becomes a decision file; its entry is marked Closed → D-0XX.
- **Staleness:** open items untouched for 3 sessions are surfaced for keep-or-kill.
