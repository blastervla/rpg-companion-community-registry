# RPG Companion – Community Registry

This repository contains the **community-maintained directory of RPG Companion repositories**.

👉 **Directory website:**  
https://repositories.rpg-companion.app

Use this registry to discover and share JSON-based RPG systems, modules and homebrew content that can be added to the **RPG Companion App**.

The data lives in [`registry.json`], which is consumed by a small website and by any external tools that want to list community repositories.

## How to add your repository

1. Fork this repository.
2. Edit `registry.json` and add a new entry:
```
   {
     "id": "unique_id_for_your_repo",
     "name": "Human-readable name",
     "description": "Short description of what your repository provides.",
     "tags": ["5e", "fantasy", "homebrew"],
     "origin": "homebrew",
     "repo_url": "https://your-host/systems/your-system/",
     "github_repo": "yourname/your-repo",  // or null if not hosted on GitHub
     "stars": 0
   }
```
3. Make sure:
   - `id` is unique and stable (e.g. `5e`).
   - `origin` is one of `official`, `published`, `homebrew` (see below).
   - `repo_url` is the URL users must paste into the RPG Companion App.
   - `github_repo` is `owner/name` if your content lives on GitHub, or `null` otherwise.
   - `stars` can be `0` – it will be updated automatically.

4. Open a Pull Request.

Once merged, your repository will appear in the community directory and its GitHub stars will be shown as “likes”.

- Your repository will appear on **https://repositories.rpg-companion.app**

## Content origin

Every entry declares an `origin` describing where its content comes from:

- **`official`** — a faithful recreation of official publisher material for the pack's
  system: WotC or Paizo rulebooks, adventures, and Unearthed Arcana. Straight ports
  between editions (e.g. bringing a 5e feat to 5e2024) count; packs that mix in your
  own creations do not.
- **`published`** — a recreation of commercial third-party material (DMs Guild,
  Kickstarter books, MCDM, Kobold Press, and the like).
- **`homebrew`** — original fan-made content. Most packs are this, and that's great —
  it's what a community registry is for.

`origin` is a **verified claim, not a search tag**: maintainers check it when reviewing
your PR and may correct it. If you're unsure, leave it as `homebrew` — an entry with no
`origin` at all is treated as `homebrew` by the app. Note that `homebrew` in `tags` is
just a search label and is unrelated to this field.

## Language

Entries are assumed to be in English. If your pack is in another language — whether a
translation or originally written in it — add a `language` field with the two-letter
[ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) code, right after
`origin`:

```json
"language": "ru"
```

Language and origin are independent: a faithful Russian translation of the 5e rules is
`"origin": "official"` **and** `"language": "ru"`. Don't add `"language": "en"` to
English packs — absent means English.

## Systems

Every entry declares which game system(s) its content is for, using the system **ids**
from the repo's own `systems.rpg` index (the app matches these exactly):

```json
"systems": ["5e2024"]
```

Most packs serve one system; a repo that has been published to from more than one
system lists them all. Current ids in the registry: `5e`, `5e2024`, `pf2e`, `5e-ru`,
`returner-system`. The app uses this to put packs for your current system first — an
entry without it sorts with "other systems", so fill it in. Packs published from the
RPG Companion App set it automatically.

## How the star sync works

A GitHub Action runs periodically and:

- Reads `registry.json`
- Queries the GitHub API for each `github_repo`
- Updates the `stars` field accordingly
- Commits the changes back if there are any

You don't need to do anything special – just set `github_repo` correctly.

