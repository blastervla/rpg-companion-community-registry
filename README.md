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
     "repo_url": "https://your-host/systems/your-system/",
     "github_repo": "yourname/your-repo",  // or null if not hosted on GitHub
     "stars": 0
   }
```
3. Make sure:
   - `id` is unique and stable (e.g. `5e`).
   - `repo_url` is the URL users must paste into the RPG Companion App.
   - `github_repo` is `owner/name` if your content lives on GitHub, or `null` otherwise.
   - `stars` can be `0` – it will be updated automatically.

4. Open a Pull Request.

Once merged, your repository will appear in the community directory and its GitHub stars will be shown as “likes”.

- Your repository will appear on **https://repositories.rpg-companion.app**

## How the star sync works

A GitHub Action runs periodically and:

- Reads `registry.json`
- Queries the GitHub API for each `github_repo`
- Updates the `stars` field accordingly
- Commits the changes back if there are any

You don't need to do anything special – just set `github_repo` correctly.

