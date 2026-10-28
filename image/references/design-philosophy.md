# Design Philosophy — Art Pieces, Abstract Posters, Series Themes

Load this when the request is an art object rather than a depicted scene: an abstract or conceptual poster, a gallery print, an album or book cover with no literal brief, a "make something beautiful about X" request, or a series of images that must share one visual identity. For product shots, portraits, and anything that must pass as a photograph, use the pattern files and [de-slop.md](de-slop.md) instead.

The failure this file prevents: the model is handed a topic and illustrates it literally. A poster "about memory" gets a brain, an hourglass, and a faded photo. The fix is to decide the aesthetic first, as its own artifact, and let the topic enter quietly afterwards.

---

## Step 1 — Write the movement before the prompt

Before any prompt, write a short design philosophy as if founding an art movement. It is a working document for you and the user, not prompt text.

**Name it** in one or two words: "Concrete Poetry", "Chromatic Silence", "Field Notation". The name is a commitment device — if a later choice does not belong to the named movement, cut it.

**Describe it in four short paragraphs, one per axis, each axis said once:**

1. **Space and form** — grid or no grid, density vs. emptiness, where the weight sits, what shapes are allowed.
2. **Color and material** — the palette as hex values with roles (ground, field, accent, ink), and what the surface is made of: risograph paper, enamel, raw canvas, backlit film.
3. **Scale and rhythm** — the ratio between the largest and smallest element, repetition, intervals, what repeats and what breaks the pattern once.
4. **Text** — how much (usually almost none), what size relationship to the image, and what role: whispered label, single monumental word, systematic reference marks.

Keep it topic-free. A good philosophy could be reused for a different subject; that is the test that it describes an aesthetic, not an illustration.

**Condensed examples** (real ones are four short paragraphs):

- **Concrete Poetry** — monumental color blocks, one huge word against tiny labels, brutalist spatial division. Meaning carried by weight and tension, never by explanation.
- **Chromatic Language** — color zones as the information system, geometric precision, small sans-serif labels anchoring what the color already says.
- **Analog Meditation** — paper grain, ink bleed, vast negative space, type whispered at the margin, one image breathing across the field.
- **Field Notation** — the subject documented as if by an imaginary science: dense repeated marks, numbered specimens, clinical micro-typography, reference ticks along the edges.

Show the name and the four lines to the user before generating when the brief is open-ended. Changing a philosophy costs one message; changing a finished series costs a re-roll of every image.

---

## Step 2 — Hide the topic inside the form

The topic is not the subject of the image; it is a reference embedded in it. Someone who knows the topic should feel it; someone who doesn't should still see a complete composition.

Translate the topic into one or two structural decisions, not objects:

| Brief | Literal (avoid) | Embedded (prefer) |
|---|---|---|
| Poster about memory | brain, hourglass, faded photo | the same form repeated with decreasing opacity across a grid; one cell left empty |
| Jazz festival | saxophone, notes | irregular rhythm of color bars with one off-beat interval; type set on a slight swing |
| Climate report cover | melting ice, thermometer | a gradient field that warms row by row; a single marker where the line crosses |
| Tea house identity | teacup, leaves | two tones bleeding into each other like steeping; a large still area of negative space |

State the embedded idea in the prompt as a structural instruction ("the grid's opacity decreases from top-left to bottom-right, one cell is empty"), never as a symbolic one ("evoking memory and loss").

---

## Step 3 — Write the prompt from the philosophy

Convert each axis into concrete visual properties. The philosophy is allowed to be poetic; the prompt is not.

- **Craft as properties, not praise.** The source method asks the result to look labored over by a master. Image models punish the words for that ("masterpiece", "stunning", "award-winning" — see [gpt-image.md](gpt-image.md) and [de-slop.md](de-slop.md)). Name what mastery looks like instead: "all elements aligned to a 12-column grid with equal 64px gutters", "consistent 2px line weight throughout", "type kerned optically, baseline-aligned across columns", "ink density even across the print".
- **Containment is a hard constraint.** Every element inside the canvas with a defined margin; nothing touching or crossing the edge unless the philosophy demands a bleed; no overlapping text. Write it in Constraints (GPT Image) or as a closing sentence (Nano Banana): "all elements contained within a 6% margin, text never overlaps other elements".
- **Text stays minimal and quoted.** A few words at most, in quotes, with typeface character and size relationship described. Follow [text-rendering.md](text-rendering.md) for exact rendering.
- **Limited palette, by hex and role.** Three to five colors, each assigned a job. An unassigned color is the one the model will overuse.
- **Repetition over invention.** Systematic, repeated elements read as deliberate; many unrelated motifs read as generated.

---

## Step 4 — Refine, don't add

When the first result is close but not right, the instinct is to add: another shape, a texture, a second accent. Resist it. The second pass removes and tightens.

Ask of every iteration: *how do I make what is already here more coherent?* Typical refining edits, one per iteration (see [golden-rules.md](golden-rules.md) — edit, don't re-roll):

- Align the stray element to the grid it almost sits on.
- Remove the one motif that does not belong to the named movement.
- Reduce the palette by one color.
- Increase the size contrast between the largest and smallest element.
- Pull a crowded element back inside the margin.

If an edit adds a new element, it needs a reason in the philosophy, not in taste.

---

## Series — one theme card, applied identically

For a set of images that must read as one family (campaign, cover series, social grid, book chapters), compress the philosophy into a **theme card** and paste it verbatim into every prompt of the series:

```
Theme: <name>
Palette: ground #____, field #____, accent #____ (accent only on <rule>), ink #____
Type: headings <character, weight, case>; labels <character, size relationship>
Surface: <material and texture, one line>
Composition rule: <the one structural rule every image obeys>
Variation allowed: <what may change per image — subject, crop, one color swap>
```

Rules for a series:

- **Offer, then wait.** When no theme is given, propose two or three named theme cards that suit the brief and let the user choose before generating. If none fits, write a custom one from their description, show it, and get confirmation.
- **Fixed means fixed.** Palette roles, type character, and surface do not change between images. Variation lives only in the line marked *Variation allowed*.
- **First image is the reference.** After the first approved image, attach it as a reference to the rest (role: style reference — see the reference-image sections of the model files) instead of relying on text alone.
- **Treat later images as pages of one book.** Each one a distinct take on the same philosophy, not a recolor of the first.

For slide decks, the named deck styles in [slides.md](slides.md) already serve as theme cards — use them there.

---

*Adapted — rewritten, not copied — after studying the `canvas-design` and `theme-factory` skills in [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) (Apache License 2.0).*

*Author: Serge Shima ([t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)) · License: CC BY 4.0 — attribution required · Source: [smixs/visual-skills](https://github.com/smixs/visual-skills)*
