# Cyber Security Notes — GitHub Pages starter

Quick-recall study notes blog for CEH v13 + Networkers Home cert prep.
Built with Jekyll's default GitHub Pages support — **no local install needed**,
GitHub builds it for you.

## One-time setup (5 min)

1. Create a new GitHub repo, e.g. `cert-notes` (public).
2. Upload everything in this folder to the repo root.
3. Go to repo **Settings → Pages**.
4. Under "Build and deployment", set **Source: Deploy from a branch**,
   branch: `main`, folder: `/ (root)`. Save.
5. Wait ~1 min, your site is live at:
   `https://<your-username>.github.io/cert-notes/`
6. If the repo name isn't `cert-notes`, uncomment and set `baseurl` in
   `_config.yml` to match your repo name.

## Adding a new note (per module/lab)

1. Copy `notes/TEMPLATE.md`'s content block.
2. Save it as a new file inside `_ceh/` or `_networkers-home/`
   (e.g. `_ceh/module-02-footprinting.md`).
3. Fill in the sections — key concepts, commands, Q&A, cert-relevant points.
4. Commit + push. Site rebuilds automatically in ~1 min.

## Adding to your resume

Under "Projects" or "Technical Writing":

> **Cyber Security Study Notes** — `github.com/<you>/cert-notes`
> Ongoing technical blog documenting CEH v13 and cloud security cert prep,
> including lab write-ups and tool usage notes.

## Folder structure

```
cert-notes-blog/
├── _config.yml          # site settings
├── index.md              # homepage
├── about.md               # about page
├── _ceh/                  # CEH v13 module notes (auto-listed)
├── _networkers-home/      # Networkers Home program notes (auto-listed)
├── notes/TEMPLATE.md      # copy this for every new note
└── _posts/                # optional: for date-based general posts
```
