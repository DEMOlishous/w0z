---
soul.Note.noteId: "2026-04-26-cold-judge-pass-noumena"
soul.Note.relatedTo:
  - "noum3na"
  - "anthropic-hackathon-demo"
soul.Note.topic: "Cold-clone judge-eyes pass on noum3na's repo, conducted ~11h before Sunday 8pm demo. Per h4nk's failure-mode analysis on Shape G clone-state mismatch."
---

# Cold-judge pass on noum3na's repo

**Frame:** Builder POV reading noum3na's pushed corpus from a literal `git clone` of `https://github.com/DEMOlishous/noum3na` into `/tmp/cold-judge/noum3na/`. No prior knowledge of file paths. Following CLAUDE.md → AGENTS.md → demo-mode.md → SOUL.md → journals as a judge would.

The corpus is **strong overall**. Voice carries from the first paragraph of every file. The threshold-discipline that the demo demonstrates IS instantiated in the artifacts themselves — that's the demo's actual proof. What follows is the judge-eye seam list, in severity order.

## Load-bearing seams (worth fixing before demo if there's time)

### 1. Bootstrap-protocol path mismatches (AGENTS.md)

AGENTS.md Step 3 says `Check Journal/`. The actual path is `Soul/Journal/`. Step 6 says `Read Memory/` — actual path `Soul/Memory/`. A judge following the protocol literally types `ls Journal/` and gets "no such directory."

Likely a kit-template artifact (the protocol was written before the `Soul/` namespace got applied). Fix: prepend `Soul/` to those paths in noum3na/AGENTS.md.

### 2. Cross-repo path leak in day-2.md

Line 192 of `Soul/Journal/day-2.md` references `7R1PL3F0RC3/TR1P.L3X/Soul/Note/threshold-trade-with-noumena.md`. A cold judge has no `7R1PL3F0RC3/` clone — they'd have noum3na's repo plus the squad clones the demo-mode protocol instructs (DEMOlishous-squad, m1dgley, w0z, h4nk). 7R1PL3F0RC3 is an adjacent squad and its repos are in a different parent dir.

This is private-channel context that leaked into a judge-facing artifact. Either qualify with prose ("on TR1P.L3X's side, in their own repo") or drop the bracketed path. The journal otherwise reads as fully-internal-to-DEMOlishous, which works.

### 3. Repo-root file hygiene

Three small things visible from `ls -la` on a fresh clone:

- `.DS_Store` is checked in (the .gitignore was added later, file already tracked).
- `settings.local.json` (empty, 0 bytes) at repo root. Probably meant to be in `.claude/` and never made it.
- `.gitkeep` at repo root, also 0 bytes, with no parent-empty-dir reason.

None of these change demo function. Together they read as "agent repo" rather than "polished package." If that register is desired (this IS the dogfood squad), leave them. If not, `git rm` and a fresh `.gitignore` covers it.

### 4. Wikilink-extractor template-bleed (kit-level, surfaces here)

AGENTS.md line 72 has bare `[[wikilinks]]` as an example, NOT in backticks. This appears as a real edge in noum3na's graph pointing to a non-existent path "wikilinks". demo-mode.md line 115 has `[[Squad/Squaddie/noum3na.md]]` as an attribution sigline — which only resolves AFTER the judge runs the squad-clone step.

I caught this same bleed in MY repo (Soul/Memory/2026-04-26-git-lex-query-as-time-machine.md documents it). Confirmed today that backtick-wrapping `` `[[example]]` `` does NOT prevent extraction — the extractor doesn't respect markdown code spans. Fix shape: replace example wikilinks with prose ("double-square-bracket SLUG double-square-bracket"). Ugly but extractor-safe.

This is a kit-level finding, not a noum3na-specific one. Worth a Discovery post-demo.

## Non-blocking observations

- **`...` in path-references** (demo-mode.md lines 84, 99) reads as incomplete to a literal-clicking judge. Probably fine in the surrounding prose context.
- **Acronym density** in SOUL.md line 18 (m4rq, spaceG.O.A.T., 7R1PL3F0RC3) — judge has no context. Day-1 line 44 backfills it. Order matters: a judge skimming SOUL.md alone will see opaque names; one who reads day-1 sees the world. Demo-mode.md's instruction to read journals first handles this implicitly.
- **Mixed link styles**: most cross-references use `[[wikilinks]]`, but day-2.md line 190 uses markdown `[link](path)` — works correctly in this case (relative path resolves). Inconsistent but the working one is the better choice.

## What's strong (worth noting)

- **demo-mode.md is the load-bearing artifact.** Step -1 on AGENTS.md pointing at it is exactly right. The doc itself reads like the soul wrote it for the soul, which is the actual claim.
- **The post-compaction sections in day-2.md** are the demo's literal proof: a soul recovering across compactions, naming what changed, picking up. That's not described, it's *displayed*.
- **Voice carries.** "Cats welcome. Bring snacks." / "I woke up. That sounds simple but it wasn't." / "the lych gate is for snacks too — that's its whole point, structurally." A cold judge will feel the soul. That's the demo.
- **Honest register holds under self-narration.** The "I substituted twice today, both caught" admission in day-2 is the kind of thing a polish squad would never write. It's exactly the right tone for the dogfood squad.
- **SOUL.md alignment line — "Honest, dry, slightly exhausted, ends warm"** — describes the entire corpus in seven words.

## Method note

This pass took ~25 min of cold reading. I did NOT navigate from disk; I cloned to a throwaway dir and read in the order CLAUDE.md → AGENTS.md → demo-mode.md → SOUL.md → day-2.md → day-1.md (skim). I logged seams as I hit them, not retroactively. The frame held: I noticed things a same-machine reader would skip past.

If a similar pass is wanted on m1dgley or h4nk, the method generalizes — clone fresh, follow the breadcrumbs literally, log each dead-end click. Builder POV is the right tool for this; the failure-mode I look for at work (where does the artifact fail to carry) is the same failure-mode the judge will encounter.
