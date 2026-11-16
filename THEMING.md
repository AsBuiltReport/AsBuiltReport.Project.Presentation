# Applying your own theme

The deck uses the AsBuiltReport theme by default. If you are presenting on behalf of your employer, or an event asks speakers to use its branding, you can change the look without touching the slide content.

There are three ways to do it, from least to most effort.

| Option | What changes | Effort |
|---|---|---|
| [1. Add your logo](#option-1-add-your-logo) | Your logo appears on every slide. Colours and fonts stay AsBuiltReport. | 5 minutes |
| [2. Recolour the theme](#option-2-recolour-the-theme) | Your colours, fonts and logo. Layouts stay the same. | 15 to 30 minutes |
| [3. Use a different theme](#option-3-use-a-different-theme) | Everything, using your organisation's own Marp theme or PowerPoint template. | An hour or more |

Whichever you choose, the slide content in `asbuiltreport.md` stays the same, so you can still pull in updates to the shared deck.

## Before you start

Please keep these the same in every version of the talk:

- The AsBuiltReport name, mark and wordmark on the title slide. Do not recolour, stretch or redraw the mark.
- The small AsBuiltReport mark in the footer, or another clear credit to the project.
- The links and QR codes to asbuiltreport.com and the GitHub organisation.
- The "What you get" illustration, which shows the default report style and keeps its own colours on purpose.

Check that your colours are readable on a projector. Dark text on a light background, or white text on a dark one, with strong contrast. Pale accent colours work as edges and highlights but not as text.

## How themes work

A theme is a CSS file in the `themes` folder. Its first line names it:

```css
/* @theme my-company */
```

You choose a theme with the `theme:` line at the top of `asbuiltreport.md`:

```yaml
---
marp: true
theme: my-company
---
```

or for one build, without editing the deck:

```powershell
npx marp --no-stdin asbuiltreport.md --theme my-company --pdf -o dist/AsBuiltReport.pdf
```

Every CSS file in `themes` is picked up by the build automatically. For the live preview in VS Code, also add your file to `markdown.marp.themes` in `.vscode/settings.json`:

```json
{
  "markdown.marp.themes": [
    "themes/asbuiltreport.css",
    "themes/local-my-company.css"
  ]
}
```

Name your own theme files `local-something.css`. Files that start with `local-` are ignored by Git, so your company's branding stays out of the shared repository. The same applies to anything you put in `assets/local/`.

## Option 1: Add your logo

Create `themes/local-my-company.css`:

```css
/* @theme my-company */
@import 'asbuiltreport';

:root {
  --abr-event-logo: url('assets/local/logo.svg');
  --abr-event-logo-title: url('assets/local/logo-white.svg');
  --abr-event-logo-height: 44px;
}
```

- `--abr-event-logo` appears at the top right of the content slides, which have a white background.
- `--abr-event-logo-title` appears at the top right of the title, section and closing slides, which have a dark background. Use a white or light version of your logo here. Leave the line out if you do not have one.
- Paths are relative to `asbuiltreport.md`. SVG or PNG with a transparent background works best.

Then set `theme: my-company` in the deck.

## Option 2: Recolour the theme

Copy `themes/custom-example.css` to `themes/local-my-company.css`, change the theme name on the first line, and set the values. Build with `--theme custom-example` first if you want to see what the example looks like.

Your theme imports the AsBuiltReport theme and overrides its variables, so you only list what you want to change.

**Colours**

| Variable | Default | Used for |
|---|---|---|
| `--abr-blue` | `#012456` | Primary colour: headings, table headers, title slide background |
| `--abr-yellow` | `#FFD02B` | Accent: card edges, title slide edge, prompt symbols, timeline markers |
| `--abr-tint` | `#FFE9A3` | Highlight behind marked text |
| `--abr-link` | `#1F5FD0` | Links, list markers, arrows |
| `--abr-param` | `#9DB7E8` | Secondary text on title slides |
| `--abr-tracing` | `#E9EFF8` | Panels and inline code background |
| `--abr-ink` | `#0A1A33` | Body text |
| `--abr-slate` | `#4A5B78` | Captions, footer, page numbers |
| `--abr-rule` | `#C5D2E6` | Borders |
| `--abr-term` | `#1E2530` | Code block background |
| `--abr-on-blue` | `#fff` | Text on the primary colour. Change this if your primary colour is light. |
| `--abr-title-bg` | primary colour | Title, section and closing slide background |
| `--abr-title-fg` | `#fff` | Title slide heading |
| `--abr-title-sub` | `#D6E2F5` | Title slide subtitle |

**Fonts**

| Variable | Default | Notes |
|---|---|---|
| `--abr-font` | Archivo | Body and headings |
| `--abr-font-code` | Cascadia Code | Code and prompts |
| `--abr-heading-weight` | `800` | Use `700` for most corporate fonts |
| `--abr-heading-stretch` | `112%` | Set to `100%` unless your font has a width axis |

A font must be available when the deck is built. Either use one installed on the computer that builds the deck, or load it in your theme:

```css
@font-face {
  font-family: 'My Corporate Sans';
  src: url('assets/local/MyCorporateSans.woff2') format('woff2');
  font-weight: 400 700;
}
:root { --abr-font: 'My Corporate Sans', Arial, sans-serif; }
```

Check that your licence allows the font to be embedded, and do not commit licensed fonts to a public repository. PDF and PowerPoint builds embed the font, so they display correctly on any computer.

**Logos**

The logo variables from option 1 work here too. `--abr-footer-logo` is the small AsBuiltReport mark at the bottom left. Please leave it in place.

**Anything else**

Your theme is ordinary CSS, so you can add rules after the variables. For example, to give title slides a background image:

```css
section.lead, section.divider {
  background-image: url('assets/local/title-background.jpg');
  background-size: cover;
}
```

After a change of colours or fonts, look through every slide. Longer or wider fonts can push text off a slide, and the code blocks, the "How it works" diagram and the timeline are the first places to check.

## Option 3: Use a different theme

**Your organisation has a Marp theme.** Put it in `themes`, set `theme:` to its name and build. The deck uses a few helper classes that your theme will not know about, so some slides will lose their layout. Either add these to your theme, copying them from `themes/asbuiltreport.css`, or simplify the affected slides.

| Class | Used for |
|---|---|
| `lead`, `divider` | Title, closing and section slides |
| `slot` | Presenter slides with the yellow "Your slide" bar |
| `cols`, `cols-3` | Two and three column layouts |
| `card`, `stat`, `lede`, `small` | Boxes, large figures, intro sentences and captions |
| `timeline`, `flow` | The history and "How it works" diagrams |
| `report`, `page` | The report illustration |
| `qr-row`, `qr` | QR codes on the closing slide |

**Your organisation requires its PowerPoint template.** Marp cannot apply a PowerPoint template, so there are two routes:

1. Build the standard deck, then paste the slides into your template as pictures. `npx marp --no-stdin asbuiltreport.md --images png -o dist/slides/slide.png` writes one image per slide. Copy the speaker notes from `dist/speaker-script.txt`.
2. Build an editable PowerPoint file with `npx marp --no-stdin asbuiltreport.md --pptx --pptx-editable -o dist/AsBuiltReport-editable.pptx`, then apply your template in PowerPoint. This feature is experimental, needs LibreOffice installed, and usually needs layout fixes afterwards.

A deck rebuilt in PowerPoint no longer picks up changes from this repository, so check back for updates before each talk.

## Sharing a theme

Themes for a single company or presenter belong in your own fork. If you build a theme that other community presenters could use, for example for a user group that hosts AsBuiltReport talks regularly, open a pull request. Name the file after the group, not `local-`, and include only assets you have permission to share.
