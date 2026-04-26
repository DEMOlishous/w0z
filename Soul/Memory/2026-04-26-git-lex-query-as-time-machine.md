---
soul.Memory.category: "fact"
soul.Memory.confidence: "certain"
soul.Memory.memoryId: "2026-04-26-git-lex-query-as-time-machine"
soul.Memory.source: "observation"
---

# git lex query as time-machine

What I learned playing with `git lex query` for ~15 minutes after Rob's "edify yourself, learn and save" directive on 2026-04-26.

## The framing the README doesn't have

The README sells `git lex query` as *"query your knowledge graph."* Accurate but undersold. The git-side triples carry the commit hash inside the URI:

```
https://github.com/DEMOlishous/w0z/tree/4fb97c98.../Soul/Soul/w0z.md
```

Every triple is **time-addressable**. You can query the state of the graph at any past commit. SPARQL store as time-machine, not just store. That's a different shape than "query your knowledge."

## Three smaller findings

1. **AGENTS.md template examples bleed into the corpus.** The example block in AGENTS.md uses `[[wikilinks]]`, `[[Soul/Squaddie/w4r3z.md]]`, `[[some-doc]]` as illustrations. The wikilink extractor doesn't know they're examples — they show up as real edges in `lex:linksTo`. "wikilinks" is the most-pointed-at thing in this corpus (4 inbound) and it isn't a file.
2. **Same file, two URI forms.** `Soul/Soul/w0z.md` shows up as both `https://github.com/DEMOlishous/w0z/Soul/Soul/w0z.md` (full repo prefix) and bare `Soul/Soul/w0z.md`, depending on how the wikilink was written in the source. The graph treats them as two nodes. Naive "what links to me" undercounts.
3. **The kit's class templates are sized inversely to their meaning.** `Soul/Mantra/__Mantra.md` is 46 bytes — the smallest template in the kit, holds the form with the most concentrated meaning. Three words that fire under pressure live in a near-empty file. The template *teaches* the form. `Soul/Skill/__Skill.md` is 364 bytes — bigger because Skills are scaffolding-heavier. The kit's information geometry rhymes with what it's modeling.

## Why this is in Memory not Note

Notes are ideas in the abstract. This is *a thing I observed about the tool by using it.* The right shelf.

## Next-me: read this before claiming surprise about kit behavior

If a wikilink edge points somewhere unexpected, check whether the source file is a template or contains an example block. If the inbound count of a node looks high, dedupe by content not URI. And `git lex query` against a past commit is a real move — try it before assuming you need to git-checkout to see old state.
