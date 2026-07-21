# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"Μικροί Ήρωες" (SRD Kids Greek) is a static, buildless content package: a
complete, Greek-language, kid-friendly tabletop RPG built entirely from Open
Game Content (SRD 5.1). No Wizards of the Coast trademarks or Product
Identity terms ("Dungeons & Dragons", "D&D", "5e", world/character names,
etc.) may appear anywhere in generated content — `OGL.md` is the source of
truth for the license this project ships under, and every deliverable's
footer links back to it.

There is no application code to run — the repo *is* the deliverable
(Markdown + print-ready HTML + CSV data + a standalone HTML tool).

## Commands

There is no package manager, build step, linter, or test suite — this is a
static content repo (Markdown, hand-authored HTML/CSS, CSV, SVG).

- **Preview a deliverable**: open its `.html` file directly in a browser
  (e.g. `open files/02_campaign/campaign.html`), or open `index.html` for
  the full navigable hub.
- **Preview/use the card generator**: `open card_generator/card-generator.html`
  — a single self-contained file, no server or install needed.
- **Export a PDF**: on request only (not committed — see `.gitignore`);
  print the relevant `.html` to PDF from the browser. There is no scripted
  export pipeline in the repo.

## Architecture

### Deliverable folders (`files/NN_name/`)

Each deliverable lives in its own numbered folder under `files/` and ships
as a **pair of files kept manually in sync**: a `.md` source (easy to edit)
and a mirrored `.html` (A4 print-ready, same visual theme). There is no
generator that produces one from the other — editing one requires updating
the other by hand. Some folders also carry a `.csv` with the deliverable's
structured stat data (`monster-stats.csv`, `spell-stats.csv`,
`items-stats.csv`) and one folder (`02_campaign`) has a `map.svg`.
`index.html` at the repo root links every deliverable and must be updated
when a new one is added.

### Shared visual theme

All `.html` deliverables and `card_generator/card-generator.html` share one
editorial theme (white/near-white surfaces, purple brand `#5a3e85`, gold
accent `#e8a93b`), but there is **no shared stylesheet** — each file defines
its own CSS custom properties (`--brand`, `--gold`, `--ink`, `--paper`, …)
in its own `:root`. Changing the theme means editing the same variables in
every `.html` file individually. Difficulty tiers, spell schools, and
character classes each keep their own distinguishable accent colors within
that shared theme.

### `card_generator/card-generator.html`

A single self-contained client-side app (no dependencies, no build, no
server) for turning CSV stat data into printable card sheets:

- User uploads one or more CSVs (monsters, spells, items, NPCs); the tool
  guesses the category from filename/header, auto-maps columns to card
  fields by alias matching, and falls back to a manual-mapping modal when it
  can't confidently match.
- Column-mapping choices and the working card library are cached in
  `localStorage` (keyed by a signature derived from the CSV header) so
  re-uploading the same shape of CSV doesn't require re-mapping.
- `card_generator/*-sample.csv` files are example/template CSVs bundled for
  users to download and fill in; they mirror the schemas the `files/03_monsters`,
  `files/04_spells`, and `files/05_handouts` CSVs use.

### Content-generation guardrails

The rest of this file governs *what* Claude should produce when asked to
generate campaign content (tutorials, characters, campaigns, monsters,
handouts, DM notes) — not how the repo's code works. Follow it for every
piece of generated content unless the user explicitly overrides it.

#### Audience & Defaults

Unless told otherwise, assume:
- Player ages: 6–12 (mixed)
- Experience level: mostly first-time players
- Group size: 3–5 players + 1 adult DM
- Session length: 60–90 minutes
- Campaign length: 3–5 sessions, short arc with a satisfying ending
- Tone: light, funny, low-stakes danger, no graphic violence or horror
- Reading level: simple sentences, minimal jargon, visuals/lists over text walls

If the user gives different numbers (age, group size, session count, theme),
use theirs instead of these defaults.

#### Deliverable Types

Treat each of these as a distinct deliverable. When asked for one, generate
only that one unless told to do the whole set.

1. **Tutorial / "How to Play" guide** — what the game is in 2–3 kid-friendly
   sentences; simplified core mechanic (roll d20 + modifier vs. a target
   number); character sheet walkthrough (Name, Class, 3–4 stats, HP, 2–3
   special moves, Inventory); how combat turns work, step by step; a short
   practice-roll exercise; a one-page DM cheat sheet of common rulings for
   kids' questions.

2. **Pre-generated characters** — 4–6 characters, each with: name, simple
   class/archetype in plain language, 3–4 stats max (plain words, not
   "STR/DEX"), 2 special abilities in plain language, a short starting
   inventory, and a one-line personality hook for roleplay.

3. **Campaign adventure document** — a story hook a kid can care about (lost
   pet, stolen pie, scared dragon, etc.); session-by-session breakdown, each
   with a goal, 2–3 key scenes (mixing exploration, roleplay, and light
   combat), at least one puzzle or creative-problem-solving moment, and a
   mini-resolution; a final climax and resolution; an NPC list with one-line
   personalities and simple performable quirks.

4. **Encounter & monster reference** — 4–6 simple stat blocks (low HP, low
   damage, one fun quirk each — favor silly or misunderstood creatures over
   scary ones), plus difficulty-scaling notes for the DM.

5. **Handouts & props** — printable character sheet template, 1–2
   illustrated prop items (map, NPC note, wanted poster), an
   initiative/turn tracker.

6. **DM quick-start notes** — pacing tips for running a session with kids,
   how to say "yes, and…" to wild kid ideas without derailing the plot, and
   guidance that failed rolls should be fun/interesting, never punishing or
   scary.

#### Style & Safety Guardrails (always apply)

- No real-world scary themes; if death comes up, keep it soft/off-screen
  ("knocked out" rather than "killed")
- No romance, no graphic violence, no profanity
- Encourage teamwork over player-vs-player conflict
- Every mechanic should give each player a chance to shine — avoid anything
  that lets one player dominate

#### Generation Order (when building an entire campaign from scratch)

1. Tutorial guide
2. Pre-generated characters
3. Campaign outline (all sessions, high-level)
4. Expand each session in detail
5. Monster/encounter reference
6. Handouts and DM notes last (they draw on everything above)

#### Defaults to Confirm When Missing

If not already specified, ask about the following — but don't block on all
of them; proceed with sensible defaults if the user just wants to get
started:
- Theme (pirates, fantasy kingdom, space, mystery, etc.)
- Exact group size and number of available sessions
- Whether handouts should be plain text or formatted for print (PDF/Word)
- Whether kids will build their own characters or use pre-gens

#### File Conventions

- Save generated content as Markdown under `files/NN_name/` at the project
  root, one numbered folder per deliverable (e.g. `files/01_tutorial/tutorial.md`,
  `files/07_characters/characters.md`, `files/02_campaign/campaign.md`,
  `files/03_monsters/monsters.md`, `files/05_handouts/handouts.md`,
  `files/06_dm_notes/dm-notes.md`). Mirror each `.md` with a print-ready
  `.html` in the same folder (A4, same visual theme — see README's
  "Χρωματικό Θέμα" section), and link both from `index.html`.
- If the user asks for a PDF, export it from the `.html` on request rather
  than by default — `.pdf` files are gitignored, not committed.
- Every `.md`/`.html` deliverable ends with a short OGL/SRD attribution
  footer pointing to `OGL.md` (see any existing deliverable for the exact
  wording) — carry it over when creating new ones.
- Keep each deliverable self-contained so it can be shared/printed on its
  own.
