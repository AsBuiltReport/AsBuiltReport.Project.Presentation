# Presenter guide

Thank you for offering to talk about AsBuiltReport. This guide helps you get from "I have the deck" to "I gave the talk" with as little effort as possible.

## Before you start

- You do not need to be an expert. If you have generated a report and found it useful, you know enough.
- The core talk is about 20 minutes. Add a demo or your own story to fill a longer slot.
- The speaker script is a starting point. Read it through, then say it in your own words. An audience can tell when someone is reading.

## Make it yours

Open `asbuiltreport.md`. Slides are separated by `---`. The text inside `<!-- -->` under each slide is the speaker script.

1. **Title slide.** Replace `Your Name`, the meetup name and the date.
2. **About me.** Replace the placeholder points, or delete the slide.
3. **Three commands.** Change `Microsoft.AD` to a product your audience uses.
4. **What you get.** If you can, swap the illustration for a screenshot of a real report from your lab. Remove anything sensitive first.
5. **Demo and How I use AsBuiltReport.** Fill these in, or delete both if you are giving the core talk only.
6. **Thank you.** Add your contact details.

Slides you are expected to change have a yellow bar across the top. To remove the bar, delete the line `<!-- _class: slot -->` at the top of that slide.

### Adding a slide

Add `---` on its own line, then write Markdown. Useful building blocks from the theme:

```markdown
---

# Slide title

<div class="cols">
<div>

Left column. Leave a blank line after each opening div so Markdown works inside it.

</div>
<div>

Right column.

</div>
</div>

<!--
Your speaker notes for this slide.
-->
```

Other classes: `cols-3` for three columns, `card` for a bordered box, `stat` for a large figure, `lede` for a larger intro sentence and `small` for a caption. For a dark section slide, start the slide with `<!-- _class: divider -->`.

To add an image, put it in `assets/images/` and use `![Description](assets/images/your-file.png)`.

## Use your own branding

Presenting for your employer, or at an event with its own slide style? You can add your logo, or change the colours and fonts, by creating a small theme file. The slide content stays the same. [THEMING.md](THEMING.md) has the steps.

## Check the facts

The project changes, so check these before each talk:

- Download count and module list on [asbuiltreport.com](https://www.asbuiltreport.com)
- That the report module in your example still installs and runs
- The [activity status](https://www.asbuiltreport.com/user-guide/report-modules/overview/#activity-status) of any module you plan to recommend

If you find something out of date in the deck, please [raise an issue or a pull request](CONTRIBUTING.md).

## Giving a demo

A demo is the most convincing part of the talk, and the part most likely to go wrong.

- Use a lab or test environment. Never demo against production.
- Generate a report beforehand and keep it open in another window. If the live run fails, show that one and move on.
- Read your sample report for hostnames, IP addresses, usernames and licence keys before you put it on a projector.
- Choose HTML output for a live run. It is quicker to open than Word.
- Increase your console font size. People at the back cannot read 12 point text.
- A report against a large environment can take a long time. Use a small target, or lower the information levels in the report configuration.

## On the day

- Bring the PDF as a fallback, on your laptop and on a USB stick.
- Bring the fonts with you. The PDF and PowerPoint builds embed them, but the HTML version needs the `assets` folder next to it.
- In the HTML version press `P` for presenter view, which shows your notes, the next slide and a timer.
- Leave time for questions. The last slide's notes list the questions that come up most often.

## Afterwards

- Share your slides with the group.
- Tell the project how it went on the [discussion board](https://github.com/orgs/AsBuiltReport/discussions). Questions you could not answer are useful feedback for the deck and the documentation.
- If you improved a slide or the script, send a pull request so the next presenter benefits.
