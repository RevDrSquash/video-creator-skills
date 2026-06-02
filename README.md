# video-creator-skills

Personal Claude Code skills for YouTube video production.

## Skills

| Skill | What it does |
|---|---|
| `/create-teleprompter` | Turns a video script into a scrolling HTML teleprompter |
| `/create-slideshow` | Turns a script or notes into an HTML cue-card slideshow |

Both skills generate a single self-contained `.html` file. Open it in any browser — no server or internet connection required.

## Installation

1. Clone this repo somewhere on your machine.
2. In your Claude Code project settings, add the plugin path so Claude Code can find the skills.

## Usage

Run either skill from the Claude Code chat, optionally pasting your script inline or pointing to a file:

```
/create-teleprompter
/create-slideshow
```

Claude will ask for your script if you haven't provided one, then write the output HTML file to your current working directory.

## Keyboard shortcuts

### Teleprompter

| Key | Action |
|---|---|
| `Space` or click | Play / pause |
| `↑` / `↓` | Increase / decrease speed |
| `←` / `→` | Jump backward / forward |
| `R` | Restart from top |
| `F` | Toggle fullscreen |
| `T` | Show / hide timing panel |

### Slideshow

| Key | Action |
|---|---|
| `Space`, `Enter`, `→`, or click | Next slide |
| `←` or `Backspace` | Previous slide |
| `F` | Toggle fullscreen |
| `R` | Restart slide timer |

## License

MIT — see [LICENSE](LICENSE).
