# Adding a project to this repo

Instructions for contributing an example project, written to be followed directly by an AI agent or by a person. If you are an agent and the user asked you to add a project here, read this file first and follow it exactly.

This repo is a showcase. Someone browsing it should be able to open any folder, watch the video, understand what the project does, and load the `.tsrct` into Tesseract to take it apart. Everything below exists to keep that true.

## 1. Pick the right tier

Choose one of the three top-level folders. When a project sits between two tiers, pick the simpler one.

| Folder | Use it when | Rough shape |
| --- | --- | --- |
| `feature-examples/` | The point is a single mechanism, and you want it uncluttered. | 1 scene, 1–4 layers, 2–6 seconds. |
| `simple-projects/` | The point is a small finished piece — a title, a lower third, a sting. | 1 scene, a handful of layers, under ~15 seconds. |
| `complex-projects/` | The point is a real production — multiple scenes, footage, sound, a full edit. | Multi-scene, imported media, usually 15 seconds or more. |

A feature example answers "how do I do X?". A simple project answers "what does a finished small thing look like?". A complex project answers "how does all of this fit together?".

## 2. Create the folder

One project per folder, named in `kebab-case`, directly inside its tier folder. Do not nest projects inside other projects.

```text
<tier>/<project-slug>/
├── README.md              required — what it is, how it was built
├── <project-slug>.mp4     required — the rendered video
├── <project-slug>.tsrct   required — the editable Tesseract project
└── preview.png            recommended — a poster frame for the README
```

Name the video and project files after the folder, so `simple-projects/hello-world/` contains `hello-world.mp4` and `hello-world.tsrct`.

Required as soon as the project embeds any third-party font or media:

```text
└── licenses/              full license text for everything packaged in the .tsrct
    ├── README.md          table: what is embedded, whose copyright, which license
    └── <LICENSE>.txt      the license text itself, one file per licensed work
```

Optional extra folders, only when they genuinely help a reader:

```text
├── Assets/                source media you generated or own, worth reusing
└── .tesseract-work/       build scripts, shader sources, action JSON, prompts, notes
```

Keep `.tesseract-work/` only when it teaches something — a WGSL source worth reading, or a build script that reproduces the project. Delete scratch renders, schema dumps, and debugging intermediates.

## 3. Requirements for every project

**The `.tsrct` must be the real, editable source.** Tesseract packages fonts and media inside the document, so it opens and renders identically on someone else's machine. A project whose `.tsrct` is a single flattened image or a bare video defeats the point of the repo.

**The video must be what the committed `.tsrct` actually renders.** If you revise the project, re-export the video in the same commit. Export with:

```sh
tsrct export --project <project-slug>.tsrct --output <project-slug>.mp4
```

**Everything embedded must be yours to redistribute, and must ship its license.** This is a public repo, and `import-font` and `import-asset` copy real bytes into the `.tsrct`. Use open-licensed fonts (SIL OFL, Apache) and media you own or that is clearly licensed for redistribution. Do not package system fonts, licensed stock, or client material.

The repository's MIT license covers the project you authored. It does **not** relicense anything you embedded, and it cannot — SIL OFL fonts in particular must stay under the OFL and travel with their copyright notice and license text. So for every third-party work packaged in your `.tsrct`:

1. Put the full license text in the project's `licenses/` folder.
2. List it in `licenses/README.md` — what it is, whose copyright, which license, what it is used for.
3. Credit it in the project README.
4. Add a row for your project to the embedded-material table in [NOTICE.md](NOTICE.md).

Check the notice that actually ships inside the file rather than trusting the filename: `tsrct` packages fonts as intact font files, so their embedded copyright and license fields come along with them.

**Do not add Mirage or Tesseract branding to a project.** The TESSERACT and Mirage names and logos are trademarks and are not licensed for reuse here. Name Tesseract as the tool a project was built with; do not put a logo in the artwork or imply endorsement.

**Keep files a sensible size.** Aim for under 25 MB per file and under 50 MB per project. Prefer a shorter piece or a tighter export over a huge one. If a complex project genuinely needs more, say so in the pull request.

**No credentials, personal data, or private client work.** Check generated filenames and project notes before committing.

## 4. Write the project README

Every project folder needs a `README.md`. Keep it short — a reader should get the idea in under a minute. Use this skeleton:

```markdown
# <Project name>

<One or two sentences: what it is, how long, what it demonstrates.>

[![<Project name>](preview.png)](<project-slug>.mp4)

▶ **[<project-slug>.mp4](<project-slug>.mp4)** · 1920×1080 · 30 fps · 8s

## What's in it

- <Mechanism 1 — and what it does here.>
- <Mechanism 2 — and what it does here.>

## Files

| File | What it is |
| --- | --- |
| `<project-slug>.tsrct` | Editable Tesseract project, fonts and media packaged inside. |
| `<project-slug>.mp4` | Rendered video. |

## How it was made

<Optional. The model and the prompt, if an agent built it. See below.>

## Remixing it

<A copy-pasteable prompt showing a natural edit to this project.>

## Credits and licensing

<Who made it. Project released under the repo's MIT license.>
<Anything embedded in the .tsrct, with its own license — link to licenses/.>
```

GitHub does not render video thumbnails in file listings, so embed a poster frame linked to the video rather than relying on the `.mp4` alone. Generate one with:

```sh
tsrct preview --project <project-slug>.tsrct --time <seconds> --output preview.png
```

Scale it to about 1280px wide to keep the repo light.

### Share the prompt, if there was one

Optional, and never a condition of merging — but if an agent built the project, consider including a **How it was made** section with the prompt you used and the model that ran it. These projects exist to be opened by an agent, so the prompt is often the most transferable thing in the folder: it shows what you actually had to ask for, which is harder to reverse-engineer from a finished `.tsrct` than any keyframe is.

Include it when you can:

- **Name the model and version** — "Claude Opus 5", not "an LLM". Capability moves fast, and a prompt reads very differently depending on what ran it.
- **Quote the real prompt**, not a tidied-up one. If it took a long back-and-forth, give the opening prompt and describe how the session went rather than pasting the whole transcript.
- **Say where the work actually happened.** If you hand-built the piece, or the agent got you 70% there and you fixed the rest by hand, that is worth more than a prompt that implies one shot. Do not reconstruct a prompt that never ran.

Skip it just as freely. Some projects are hand-built, some came out of a session too long or too messy to be worth summarising, and some prompts contain things you would rather not publish. A project with no **How it was made** section is complete.

Longer material — a full transcript, a build script, intermediate prompts — belongs in `.tesseract-work/` if it teaches something, not in the README.

## 5. Update the root README

Add a row for your project to the matching table in [README.md](README.md), with the project name, the poster, and a one-line description of what it shows. If your tier still says _"Nothing here yet"_, replace that line with the table.

## 6. Check before opening a pull request

- [ ] The project is in the right tier folder, in its own `kebab-case` folder.
- [ ] `README.md`, `<slug>.mp4`, and `<slug>.tsrct` are all present and named after the folder.
- [ ] The `.tsrct` opens: `tsrct project inspect --project <slug>.tsrct` succeeds.
- [ ] The committed video is a current export of the committed project.
- [ ] You actually watched the video end to end.
- [ ] Embedded fonts and media are licensed for redistribution.
- [ ] `licenses/` holds the full text for everything embedded, and `NOTICE.md` lists the project.
- [ ] No Mirage or Tesseract logos or branding in the artwork.
- [ ] The root README lists the project.
- [ ] Optional: the README credits the model and prompt that built it, if an agent did.
- [ ] No scratch files, no credentials, no private material.
