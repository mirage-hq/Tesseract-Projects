# Tesseract Projects

Free, open example projects for **[Tesseract](https://github.com/mirage-hq/Tesseract)** — the creative suite built for your AI agent.

Every project here ships as an editable `.tsrct` document plus the video it renders to. Download one, open it with Tesseract, and ask your agent to change it. Nothing is flattened, baked, or locked: the layers, keyframes, text, and shaders are all still live.

## Getting Tesseract

Tesseract is a set of agent skills plus a local CLI (`tsrct`). Install both with:

```sh
npx skills add mirage-hq/Tesseract
```

Full instructions, downloads, and the plugin itself are in the **[Tesseract repository](https://github.com/mirage-hq/Tesseract)**. Tesseract runs locally on macOS and Windows, and is licensed under its own [terms](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md) — separate from the MIT license on the projects in this repo. See [NOTICE.md](NOTICE.md).

## How this repo is organized

Projects are grouped into three folders by what they are meant to teach.

| Folder | What lives there |
| --- | --- |
| **[feature-examples/](feature-examples/)** | One mechanism, shown in isolation — a custom WGSL shader, a track matte, a text animator, a gain envelope. The smallest thing that demonstrates the feature clearly. |
| **[simple-projects/](simple-projects/)** | A complete, short piece with a beginning and an end. A title card, a lower third, a logo sting, a captioned clip. Usually one scene and a handful of layers. |
| **[complex-projects/](complex-projects/)** | Full productions — multi-scene edits, ads, music-driven sequences, imported footage, sound design. The kind of thing you would actually ship. |

Each project gets its own folder containing a README, the rendered video, and the `.tsrct` project file. See **[AGENTS.md](AGENTS.md)** for the exact layout and how to add your own.

## Projects

### Feature examples

_Nothing here yet — [contributions welcome](AGENTS.md)._

### Simple projects

| Project | Preview | What it shows |
| --- | --- | --- |
| **[Hello World](simple-projects/hello-world/)** | <a href="simple-projects/hello-world/"><img src="simple-projects/hello-world/preview.png" width="260" alt="Hello World"></a> | An 8-second title card built from two custom WGSL shaders, keyframed type, and a per-character text animator. |

### Complex projects

| Project | Preview | What it shows |
| --- | --- | --- |
| **[Spam Showreel](complex-projects/spam-showreel/)** | <a href="complex-projects/spam-showreel/"><img src="complex-projects/spam-showreel/preview.png" width="260" alt="Spam Showreel"></a> | A 15-second, seven-scene brand reel cut to music — 1,653 layers, beat-locked expressions, 3D camera moves, and not one imported image or font. |

## Using a project

1. Install Tesseract (above).
2. Clone this repo, or download the folder for the project you want.
3. Point your agent at the `.tsrct` file and describe the change:

```text
Open simple-projects/hello-world/hello-world.tsrct with Tesseract.
Change the headline to "Good morning" and make the background
warmer — amber instead of indigo. Render a preview, then export.
```

Each `.tsrct` is self-contained: fonts and media are packaged inside it, so a project renders the same on any machine with Tesseract installed.

## Contributing a project

Read **[AGENTS.md](AGENTS.md)**. It defines the folder layout, naming, and the checks a project needs to pass — written so that either a person or an agent can follow it directly. In short: pick the right tier, give the project its own folder, include the README, the video, and the `.tsrct`, and make sure anything embedded in the project is yours to share.

If an agent built your project, consider saying so in its README — which model, and the prompt you gave it. It is optional and not a condition of merging, but these projects are meant to be opened by an agent, and the prompt is often the most useful thing in the folder: it shows what you actually had to ask for, which no amount of reading the `.tsrct` will tell you.

## Licensing

**The example projects in this repository are free to use.** The projects, videos, and documentation here are released under the [MIT License](LICENSE) — use them, remix them, ship them, commercially or otherwise.

Three things are *not* covered by that license, and it is worth being clear about them:

- **Tesseract itself is not in this repository and is not MIT licensed.** It is proprietary software owned by Mirage, under its own [terms and conditions](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md). You need it to open a `.tsrct`, and those terms govern that use — including conditions on commercial use above a revenue threshold.
- **The TESSERACT and Mirage names and logos are trademarks.** MIT covers copyright, not trademarks. Say what your project was made with; don't imply endorsement.
- **Fonts and media embedded inside a `.tsrct` keep their own licenses.** Each project that packages third-party material ships a `licenses/` folder alongside it.

See **[NOTICE.md](NOTICE.md)** for the full explanation.
