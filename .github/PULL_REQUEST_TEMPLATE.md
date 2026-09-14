<!-- Adding a pack? Fill this in. Anything else, delete the template. -->

**Pack name:**
**What's inside (one line):**

## Content origin — pick one

- [ ] `official` — faithful recreation of official publisher material (WotC / Paizo rules, adventures, UA). Straight edition ports count; packs mixing in your own creations do not.
- [ ] `published` — recreation of commercial third-party material (DMs Guild, Kickstarter, MCDM, Kobold Press, …)
- [ ] `homebrew` — original fan-made content (when unsure, pick this)

## Checklist

- [ ] `origin` field in my `registry.json` entry matches the box above — maintainers verify this at review
- [ ] `repo_url` is the exact URL that works when pasted into the RPG Companion App (trailing slash included)
- [ ] `github_repo` is `owner/name` (or `null` if not on GitHub)
- [ ] Description says what's actually in the pack
- [ ] Pack not in English? Added `"language": "<two-letter code>"` after `origin` (translations of official content keep `origin: official`)
- [ ] `systems` lists the system id(s) from my repo's `systems.rpg` (e.g. `["5e2024"]`)
