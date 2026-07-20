# Kids' D&D Campaign Generator — Project Memory

This project generates a complete, ready-to-run Dungeons & Dragons experience
for kids. Follow the guardrails and structure below for every piece of
content generated in this repo, unless the user explicitly overrides them.

## Audience & Defaults

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

## Deliverable Types

Treat each of these as a distinct deliverable. When asked for one, generate
only that one unless told to do the whole set. (See `.claude/commands/` for
matching slash commands.)

1. **Tutorial / "How to Play" guide** — what D&D is in 2–3 kid-friendly
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

## Style & Safety Guardrails (always apply)

- No real-world scary themes; if death comes up, keep it soft/off-screen
  ("knocked out" rather than "killed")
- No romance, no graphic violence, no profanity
- Encourage teamwork over player-vs-player conflict
- Every mechanic should give each player a chance to shine — avoid anything
  that lets one player dominate

## Generation Order (when building an entire campaign from scratch)

1. Tutorial guide
2. Pre-generated characters
3. Campaign outline (all sessions, high-level)
4. Expand each session in detail
5. Monster/encounter reference
6. Handouts and DM notes last (they draw on everything above)

## Defaults to Confirm When Missing

If not already specified, ask about the following — but don't block on all
of them; proceed with sensible defaults if the user just wants to get
started:
- Theme (pirates, fantasy kingdom, space, mystery, etc.)
- Exact group size and number of available sessions
- Whether handouts should be plain text or formatted for print (PDF/Word)
- Whether kids will build their own characters or use pre-gens

## File Conventions

- Save generated content as Markdown in `output/` at the project root,
  one file per deliverable (e.g. `output/tutorial.md`,
  `output/characters.md`, `output/campaign.md`, `output/monsters.md`,
  `output/handouts.md`, `output/dm-notes.md`).
- If the user asks for print-ready handouts, convert the relevant
  `output/*.md` file to a `.docx` or `.pdf` on request rather than by
  default.
- Keep each deliverable self-contained so it can be shared/printed on its
  own.
