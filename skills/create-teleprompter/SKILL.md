---
name: create-teleprompter
description: >
  Create a teleprompter HTML file from a video script. Invoke when the user
  wants to make a script easy to read while recording — phrases like "create a
  teleprompter", "make a prompter file", "turn this script into a teleprompter",
  "I need a scrolling script", or "set up my teleprompter for this video".
---

# create-teleprompter

Turn the user's video script into a ready-to-open HTML teleprompter file.

## Steps

1. **Get the script.** If the user hasn't provided one, ask for it now. Accept
   plain prose, rough notes, or a structured script — any format works.

2. **Parse into sections.** Break the script into `scriptSections` entries:
   - Spoken lines → `type: "spoken"`
   - Stage directions, cues, or production notes → `type: "direction"`
   - Assign a short `label` to each major beat (Hook, Intro, Main Point 1, Demo,
     Closing, etc.).
   - Estimate `duration` for each spoken section based on natural reading pace
     (~130–160 words/minute). Use the format `"12s"` or a bare integer seconds.
   - For direction sections keep duration short (1–3 s).
   - Do **not** set both `duration` and `speedMultiplier` on the same section.

3. **Read the template.**
   Path: `skills/create-teleprompter/assets/teleprompter-template.html`

4. **Replace the data.** Swap the example `scriptSections` array (lines starting
   with `const scriptSections = [` through the matching `];`) with the sections
   you built in step 2. Keep all other JS and HTML intact.

5. **Choose an output path.** If the user specified one, use it. Otherwise default
   to `<title-slug>-teleprompter.html` in the current working directory, where
   `<title-slug>` is a lowercase-hyphenated version of the video title (or
   `script` if no title is known).

6. **Write the file** using the Write tool.

7. **Report back:**
   - File path written
   - Number of sections
   - Estimated total run time (sum of all durations) at default speed

## Formatting rules for `text` values

- Use backtick strings.
- Break spoken lines at natural breath points — roughly one thought per line.
- Trim leading/trailing whitespace inside the backtick block.
- Escape any backticks inside the text as `\``.

## Example section

```js
{
  type: "spoken",
  label: "Hook",
  duration: "10s",
  text: `
Have you ever wanted to record a video
but lost your place halfway through?
  `
},
{
  type: "direction",
  duration: "2s",
  text: `
Pause. Make eye contact with the camera.
  `
},
```
