# wm-ai-create-guide

An AI skill for developers contributing to [wavemaker/ai-docs](https://github.com/wavemaker/ai-docs). It takes your draft content — rough notes, bullet points, anything — and produces a complete, publish-ready **Guide** page that follows the WaveMaker docs structure and conventions.

---

## Who This Is For

Developers and technical writers authoring guide pages for [docs.wavemaker.ai](https://docs.wavemaker.ai). If you're adding a new how-to or tutorial under `docs/guide/` in the ai-docs repo, this skill does the heavy lifting so you don't have to think about MDX structure, frontmatter fields, or sidebar wiring.

---

## Installation

```sh
npx skills add wm-artifacts/wm-ai-create-guide
```

The skill is picked up automatically by any AI assistant that supports npm-based skills.

---

## Usage

### 1. Give it your draft

Invoke the skill and paste whatever you have. It accepts any form:

- Bullet-point steps
- Rough prose notes
- A partially written doc
- Just a title and a loose description

### 2. Answer one round of questions

The skill reviews your draft, identifies gaps, and asks everything it needs in a single message — things like:

- Missing prerequisites
- Steps that need more detail
- Known limitations or gotchas
- Related docs to link
- Screenshots or GIFs (share the files and say which step they belong to)
- Academy video URL — if there's a walkthrough on [academy.wavemaker.ai](https://academy.wavemaker.ai), share the link and it gets embedded as a `<VideoCard>`
- **Author name** — always required for the frontmatter

Respond once. The skill generates the guide immediately after.

### 3. Commit the output

The skill produces two things:

1. A complete `.md` file at `docs/guide/<subfolder>/<filename>.md`
2. A sidebar entry in `guideSidebar.js` — so the page appears in navigation

Review, adjust if needed, then commit to your feature branch and open a PR against `main`.

---

## What Gets Generated

Every guide follows the WaveMaker docs structure:

| Section | Notes |
|---|---|
| Frontmatter | `title`, `id`, `sidebar_label`, `last_update.author` |
| Overview | 2–3 sentences, outcome-focused |
| VideoCard | Only if you provided an Academy URL |
| Prerequisites | Bulleted, with links to related docs |
| Steps | One H2 per phase, numbered atomic steps within |
| Limitations | Optional — only included if there's real content |
| See Also | 2–5 relative links to related docs |

---

## Project Files

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | The skill definition — instructions the AI follows |
| [assets/guide-template.md](assets/guide-template.md) | Base template used for every generated guide |
