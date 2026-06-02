# video-creator-skills

A Claude Code plugin with personal skills for producing YouTube videos.

## Skills

| Skill | Invocation | Purpose |
|---|---|---|
| `create-teleprompter` | `/create-teleprompter` | Turns a video script into a scrolling HTML teleprompter |
| `create-slideshow` | `/create-slideshow` | Turns a script or notes into an HTML slideshow of cue cards |

Both skills generate a self-contained `.html` file you can open in any browser — no server required.

## Plugin structure

```
video-creator-skills/
├── .claude-plugin/
│   └── plugin.json                      # Plugin manifest (name, version, author, etc.)
├── CLAUDE.md                            # This file
├── README.md                            # User-facing installation and usage docs
└── skills/
    ├── create-teleprompter/
    │   ├── SKILL.md                     # Skill definition and Claude instructions
    │   └── assets/
    │       └── teleprompter-template.html
    └── create-slideshow/
        ├── SKILL.md                     # Skill definition and Claude instructions
        └── assets/
            └── slideshow-template.html
```

## How a skill works

Each `SKILL.md` contains:
- **Frontmatter** (`name`, `description`) — the `description` field controls when Claude auto-suggests the skill.
- **Body** — the instructions Claude follows when the skill is invoked.

When a skill runs, Claude reads the relevant template from `assets/`, replaces the data array with content derived from the user's script, and writes the output HTML file.

## Developing a skill

1. Edit `SKILL.md` to refine the instructions or trigger description.
2. Edit the HTML template in `assets/` to change the visual design.
3. Test by invoking the skill with a sample script and opening the output in a browser.
4. Bump `version` in `plugin.json` when shipping a change.

## Template formats

### Teleprompter — `scriptSections` array

```js
{
  type: "spoken" | "direction",
  label: "optional heading",
  text: `multiline script text`,
  duration: "12s",          // OR
  speedMultiplier: 0.85     // one or the other
}
```

### Slideshow — `slides` array

```js
{
  html: `<h2>Heading</h2><p>Body text.</p>`,
  seconds: 20
}
```

Supported slide elements: `<h1>`, `<h2>`, `<p>`, `<ul>/<li>`, `<strong>`, `<em>`, `<p class="small">`, `<div class="callout">`.
