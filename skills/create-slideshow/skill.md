---
name: create-slideshow
description: >
  Create a slideshow of cue-card HTML slides from a video script or notes.
  Invoke when the user wants visual reference cards to glance at while recording
  — phrases like "create a slideshow", "make cue cards", "turn this into slides",
  "I need a slide deck for my video", "make a reference slideshow", or "create
  speaker notes slides".
---

# create-slideshow

Turn the user's video script or notes into a ready-to-open HTML cue-card slideshow.

## Steps

1. **Get the content.** If the user hasn't provided a script or notes, ask now.
   Accept any format: rough bullet points, a full script, or structured sections.

2. **Plan the slides.** Each slide should cover one idea or one spoken beat.
   As a guide:
   - Title/intro beat → one slide with `<h1>`
   - Major section transitions → one slide with `<h2>` heading
   - Key point with supporting detail → `<h2>` + `<p>` or `<ul>`
   - A notable quote or key takeaway → `<div class="callout">`
   - Quiet context or small print → `<p class="small">`
   Aim for 6–15 slides for a typical 3–10 minute video.

3. **Assign `seconds` to each slide.** Base it on how long you'd naturally speak
   through that content (~130 words/minute). A title slide might be 8–12 s; a
   dense bullet list might be 30–45 s.

4. **Read the template.**
   Path: `skills/create-slideshow/assets/slideshow-template.html`

5. **Replace the data.** Swap the example `slides` array (lines starting with
   `const slides = [` through the matching `];`) with the slides you built.
   Keep all other JS and HTML intact.

6. **Choose an output path.** If the user specified one, use it. Otherwise default
   to `<title-slug>-slideshow.html` in the current working directory, where
   `<title-slug>` is a lowercase-hyphenated version of the video title (or
   `script` if no title is known).

7. **Write the file** using the Write tool.

8. **Report back:**
   - File path written
   - Number of slides
   - Estimated total run time (sum of all `seconds` values), formatted as m:ss

## Supported HTML elements inside `html` strings

| Element | Use for |
|---|---|
| `<h1>` | Title slide heading |
| `<h2>` | Section heading (renders in accent blue) |
| `<p>` | Body text |
| `<strong>` | Key term or emphasis (renders in accent blue) |
| `<em>` | Lighter emphasis |
| `<ul><li>` | Bullet list |
| `<ol><li>` | Numbered list |
| `<p class="small">` | Quieter note or aside |
| `<div class="callout">` | Highlighted block quote or key takeaway |

## Example slides

```js
{
  html: `
    <h1>Semantic Search</h1>
    <p>Search by <strong>meaning</strong>, not just matching words.</p>
  `,
  seconds: 12
},
{
  html: `
    <h2>Why keyword search falls short</h2>
    <ul>
      <li>"red shirt" matches "red pants" — same word, wrong item</li>
      <li>misses "maroon blouse" — different words, same intent</li>
    </ul>
  `,
  seconds: 28
},
```
