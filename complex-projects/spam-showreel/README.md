# Spam Showreel

A 15-second brand showreel for a fictional photo app — seven scenes, cut to an original Italo-disco track, ending on a logo lockup. It is here as the "how does all of this fit together?" example: 1,653 layers, 3,843 animators, and a real edit with a beat to hit.

[![Spam Showreel](preview.png)](spam-showreel.mp4)

▶ **[spam-showreel.mp4](spam-showreel.mp4)** · 1920×1080 · 30 fps · 15 seconds

The thing worth knowing before you open it: **nothing visual is imported.** No footage, no stock images, no fonts — not even a bitmap for the logo. Every pixel on screen is vector shapes, two WGSL shaders, and JavaScript expressions evaluated per frame. The only packaged asset in the whole document is the music.

## The edit

| Time | Scene | What happens |
| --- | --- | --- |
| 0.00 – 2.41s | **S1 · Ignition** | The app icon draws itself on with trim paths, then a whip-pan rig throws it past camera on stacked colour echoes. Motion blur, directional blur, and chromatic aberration all ride the whip. |
| 2.41 – 4.44s | **S2 · Kinetic type** | Four full-bleed colour cards — SHOOT. / POST. / REPEAT. / SPAM IT. — each with its own build: pixel assembly, colour-block wipe, 3D flap with an echo stack, and a scale slam. |
| 4.44 – 6.46s | **S3 · Tunnel** | A fly-through of a corridor built from photo cards, 381 layers deep, with a custom depth-fog shader keeping the far end readable. |
| 6.46 – 8.48s | **S4 · Flyover** | The obligatory grid horizon and synth sun, with NO LIMITS assembling over it under a handheld camera shake. |
| 8.48 – 10.51s | **S5 · Product UI** | A phone mockup running the fake app — feed, likes counter ticking to 999+, a notification toast sliding in. |
| 10.51 – 12.55s | **S6 · Multiply** | One card becomes 4, then 16, then 64 on a drifting 3D grid, then implodes to a single chrome point and a flash. A slice-glitch shader tears the frame on the hits. |
| 12.55 – 15.00s | **S7 · Resolve** | Logo lockup punches in on the beat over a settling sun and grid, sparks and shock rings on the impact. |

A HUD overlay — corner brackets, REC dot, reel tag, a running timecode, and a per-scene caption — sits over the first six scenes and drops away for the end card. A global adjustment layer puts grain and a vignette over the whole 15 seconds.

## What's in it

**The type is drawn, not typeset.** There is not one text layer or embedded font in the project. Every character — the kinetic headlines, the HUD captions, the timecode digits, the tagline — is a shape layer whose path is a set of axis-aligned squares on a 4px grid. It is a hand-built pixel font made of geometry, which is why the letterforms can be lit, exploded, and flapped in 3D like any other shape.

**The timecode is a digit stack.** Each of the four timecode positions carries all ten digits as separate layers, stacked; an opacity animator on each one turns exactly the right digit on at the right frame. Forty layers to count from `00:00.0` to `00:12.5`, and no text rendering anywhere.

**Motion is mostly expressions, not keyframes.** Of 3,843 animators, 2,217 are `jsScript` — 1,753 of them distinct. They range from one-liners to ~2,800-character programs that define their own helpers inline: cubic-bezier solvers, critically damped springs, and exponential kick envelopes.

**And the expressions know where the beat is.** The kick envelopes carry the track's downbeats as literal times — `beats(t,tau) = kick(t,0.895,tau) + kick(t,1.4,tau) + kick(t,1.905,tau)` — so scale, glow, and camera push are all driven off the same rhythm the cut is built on. That is what makes the logo punches land with the music rather than near it.

**Two custom WGSL shaders, used 81 times.** Both are authored in the project with named, animatable parameters:

- `Depth fog (colour)` mixes each tunnel card toward the violet haze by distance, so the far end of S3 stays opaque instead of stacking into mush.
- `Spam slice glitch` tears the frame into horizontal bands that shift independently with a per-band RGB split — driven by `amount` and re-seeded on each hit in S6.

**Stock effects do the rest.** 159 glows, 93 gaussian blurs, plus chromatic aberration on the whips, directional blur, exposure, mosaic, grain, and vignette — 354 effect instances in total.

**Real 3D.** Layers animate on `positionZ`, `rotationX`, and `rotationY` inside camera groups, which is what the tunnel, the multiply grid, and the REPEAT. flap are all built out of.

## Files

| File | What it is |
| --- | --- |
| `spam-showreel.tsrct` | Editable Tesseract project. Every scene, shader, and expression is live; the music is packaged inside. |
| `spam-showreel.mp4` | Rendered video, H.264 + AAC, 1920×1080, 30 fps, 15s. |
| `preview.png` | Poster frame at 14.5s. |

## Remixing it

```text
Open spam-showreel.tsrct with Tesseract. Rebrand it from "SPAM" to "ECHO."
— redraw the pixel lettering in the S7 lockup and the S2 "SPAM IT." card,
and shift the palette from magenta/cyan to lime and deep teal, keeping the
sun and grid. Leave every beat time alone. Render a filmstrip of S7, then export.
```

Good places to start if you just want to take it apart:

- **Solo a scene.** `tsrct filmstrip --project spam-showreel.tsrct --fx-solo main:30000` renders the tunnel on its own over its active window.
- **Retime the whole reel.** The beat times are literals inside the `jsScript` animators. Change the track and you change those numbers — that is the real work in a music-cut piece, and this project shows exactly where it lives.
- **Turn up the glitch.** Raise `amount` on the `Spam slice glitch` shader in S6 past 0.1 and the implode gets much nastier.
- **Steal the HUD.** The overlay group is self-contained and sits over everything; drop it on your own footage.

## Credits and licensing

Built with [Tesseract](https://github.com/mirage-hq/Tesseract), which is licensed under its own [terms](https://github.com/mirage-hq/Tesseract/blob/main/TERMS.md) and is not part of this repository.

This project — the composition, both WGSL shaders, the expressions, the music, and the rendered video — is released under the repository's [MIT license](../../LICENSE). Use it however you like.

No third-party fonts or media are packaged in the `.tsrct`, so there is no `licenses/` folder. One thing is worth disclosing anyway: the music track is **AI-generated**, made with [Suno](https://suno.com) on a paid plan by its publisher, who owns the output under Suno's terms and releases it here under the same MIT license as the rest of the project. Note that the copyright status of AI-generated audio varies by jurisdiction — see [NOTICE.md](../../NOTICE.md).

"SPAM" here is a made-up app in a made-up showreel; the reel is not associated with any real product.
