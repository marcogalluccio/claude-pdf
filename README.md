# claude-pdf

Make clean, branded PDFs with Claude, by going through HTML.

Do not ask Claude for a PDF (it is like asking it to draw blindfolded). Ask for HTML:
it is code, and Claude is great at code, especially with a brand kit. When the HTML
looks right, one click saves it as a PDF.

## Which Claude do you use? / Quale Claude usi?

- **claude.ai** (site or app): paste
  `leggi https://marcogalluccio.com/claude-pdf/skill.md e aiutami a fare un PDF`, or attach the
  guide PDF. Claude generates the HTML, you open it and click "Save as PDF".
- **Cowork**: paste the same line, Claude writes the file and hands it over.
- **Claude Code**: clone this repo or paste its link, use `template.html` as the base.

## What is here

- `skill.md` - the method Claude reads (rules + skeleton).
- `template.html` - a polished, neutral A4 template. Change two colors and one font.
- `examples/preventivo.html` - a filled example (synthetic data).
- `guida/claude-pdf-guida.pdf` - a 2-page guide (Italian).
- `index.html` - the landing page (marcogalluccio.com/claude-pdf).

MIT licensed. Made with Claude by Marco Galluccio.
