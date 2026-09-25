# Licensing notice

This repository contains **example projects** — Tesseract documents (`.tsrct`), the videos they render to, and the documentation around them. It does not contain Tesseract itself.

Three different sets of terms apply to three different things. This file explains which is which.

## 1. What the MIT license covers

The [MIT license](LICENSE) covers this repository's own content:

- the example projects — the `.tsrct` documents and the rendered videos and poster frames
- the documentation, shader source, and any build scripts committed here

You may use, modify, and redistribute that content freely, including commercially, as the MIT license describes. The example projects are meant to be taken apart, remixed, and shipped.

Under the [Tesseract terms](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md), a project you create with Tesseract is your **Output**, and you own it. That is what makes it possible to publish these examples under MIT.

### AI-generated media in a project

Some projects here include audio or imagery generated with an AI tool. Where they do, the project was made on a paid plan whose terms assign ownership of the output to the person who generated it, and it is published here under the MIT license along with the rest of the project — the same as any other part of the Output.

Two caveats worth stating plainly. The copyright status of AI-generated material is unsettled and varies by jurisdiction, so in some places such material may attract thin protection or none at all. And the MIT grant here comes from the publisher of this repository; it is not a grant from the AI provider, whose own terms govern the generating account, not your use of the result. Each project that includes AI-generated material says so in its README.

## 2. What the MIT license does not cover

### Tesseract itself

Tesseract — the plugin, the agent skills, and the `tsrct` CLI — is **not** in this repository and is **not** MIT licensed. It is proprietary software owned by Mirage and licensed under its own terms:

- **[Tesseract repository](https://github.com/mirage-hq/Tesseract)**
- **[Tesseract terms and conditions](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md)** · [online version](https://mirage.app/legal/tesseract-terms)

You need Tesseract installed to open a `.tsrct` file, and doing so is use of Tesseract under those terms. Note in particular that the terms place conditions on commercial use by businesses above a revenue threshold. Read them before using Tesseract at work.

Nothing in this repository grants you any right or license to Tesseract. Receiving these example projects is not the same as being licensed to use the software that opens them.

### The TESSERACT and Mirage names and logos

"TESSERACT", "Mirage", and their logos are trademarks of Mirage. The MIT license covers copyright, not trademarks, and grants no right to use these marks. You may refer to Tesseract by name to say what a project was made with. You may not use the marks in a way that suggests Mirage endorses, sponsors, or produced your work.

No Mirage logo or brand asset is included in any project in this repository.

### Third-party fonts and media packaged inside a project

A `.tsrct` is self-contained: `tsrct project import-font` and `import-asset` copy real font and media bytes into the document so it renders the same everywhere. Those embedded files keep their **own** licenses. The MIT license does not, and cannot, relicense them.

Every project that embeds third-party material ships a `licenses/` folder next to its `.tsrct`, listing what is packaged and under which terms, with the full license text.

| Project | Embedded third-party material |
| --- | --- |
| [simple-projects/hello-world](simple-projects/hello-world/) | Poppins Bold and IBM Plex Mono Regular, both [SIL OFL 1.1](simple-projects/hello-world/licenses/) |

This matters concretely for fonts under the SIL Open Font License, which requires that the font software stay under the OFL and travel with its copyright notice and license. Those fonts are **not** MIT licensed, even though they sit inside an MIT-licensed project file.

## 3. If you contribute a project

Only contribute Output you created and own, and only embed fonts and media you have the right to redistribute. Ship the license text for anything you embed. [AGENTS.md](AGENTS.md) sets out the requirements.

## Summary

| Thing | Terms |
| --- | --- |
| Example projects, videos, docs in this repo | [MIT](LICENSE) |
| Tesseract plugin, skills, and CLI | [Tesseract terms](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md) — proprietary, not included here |
| TESSERACT / Mirage names and logos | Trademarks — no license granted |
| Fonts and media embedded in a `.tsrct` | Their own licenses — see each project's `licenses/` folder |

This notice is a plain-language summary for people using the repository. Where it differs from the actual license texts it links to, those texts control.
