# Contributing

This deck belongs to the AsBuiltReport community. If you have presented it and found something that could be clearer, more accurate or more convincing, please send the change back.

## What to contribute

- **Corrections.** Out of date figures, commands that no longer work, broken links.
- **Clearer wording** on slides or in the speaker script.
- **Better examples**, such as a more representative command or a real, sanitised report screenshot.
- **Optional slides** on topics some audiences ask for, for example custom styles, scheduling reports or writing a report module.
- **Themes** for community groups that host AsBuiltReport talks. See [THEMING.md](THEMING.md). Company themes belong in your own fork.
- **Translations** of the deck. Add them as a separate file, for example `asbuiltreport.fr.md`.

Please do not add your personal slides (your introduction, your employer, your demo) to the shared deck. Keep those in your own fork.

## How to contribute

1. Fork the repository and create a branch from `main`.
2. Edit `asbuiltreport.md`. Use the Marp for VS Code extension to preview, or run `npm run build`.
3. Check the slide in the preview. Text must not run off the slide or overlap the footer.
4. Open a pull request that says what you changed and why. A screenshot of the slide helps reviewers.

Every pull request is built automatically. Download the build from the pull request's checks to see the finished PDF.

## Guidelines

- **Keep the core talk to about 20 minutes.** If you add a slide to the core section, say what it replaces or why the extra time is worth it. New material is usually better as an optional slide.
- **Every slide needs a speaker script.** Write it the way you would say it, in short sentences, and start with a timing such as `[1.5 min]`.
- **One idea per slide.** If a slide needs more than about 40 words, split it.
- **Follow the brand.** Use the theme's colours, fonts and classes, and do not add inline colours or other fonts. The brand guidelines are in the [website repository](https://github.com/AsBuiltReport/AsBuiltReport.Project.Website#branding).
- **Be accurate and fair.** Do not overstate what the project does, and do not criticise other tools or vendors.
- **Only use material you have the right to share.** No customer data, no real hostnames or addresses, and no images you do not own.
- **Plain language.** The deck is presented around the world, often to people whose first language is not English.

## AI-assisted contributions

You may use AI tools to help write or edit content. You are responsible for everything you submit, so check facts, commands and figures yourself. The project's [AI use policy](https://www.asbuiltreport.com/dev-guide/ai-use-policy/) applies to this repository.

## Questions

Ask on the [discussion board](https://github.com/orgs/AsBuiltReport/discussions).
