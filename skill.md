# Make PDFs with Claude

A tiny method for turning any document into a clean, branded PDF, using Claude.

The trick: do not ask Claude for a PDF. Ask for HTML. HTML is code, and Claude is
great at code, especially when you give it a brand kit. When the HTML looks right,
you save it as a PDF in one click.

This file IS the skill. If you pasted a link to it, follow the steps below. Talk to
the user in their own language, and write every visible word of the document in their
language too.

## What to produce

When the user asks for a document (a quote, a proposal, a one-pager, a CV, a report,
an invoice, a letter, anything), generate ONE self-contained HTML file, page size A4,
with a built-in "Save as PDF" button. Never output a binary PDF directly.

## Rules

1. One self-contained HTML file. No external assets except a Google Font link.
2. A4 portrait. Use a `.page` element with `width:210mm; min-height:297mm`, inner
   padding around 18mm, a cream or white sheet centered on a grey backdrop.
3. A fixed "Save as PDF" button, top-right, that calls `print()`. Hide it when
   printing. Label it in the user's language (for Italian, "Salva come PDF").
4. Print rules so the PDF comes out clean:
   `@page{ size:A4; margin:0 }` plus `@media print{ .save{display:none} ... }`.
5. Brand kit at the top: CSS variables for two colors and one font. Changing those
   three values rebrands the whole document. Ask the user for brand colors; if there
   are none, pick a tasteful default.
6. One idea per section. Short headings. A clear type scale. Page numbers if the
   document runs to more than one page.
7. Editorial look: generous whitespace, a thin accent rule, aligned columns for any
   table. No clip-art, no emoji inside the document.
8. No em-dash and no double hyphen in the copy. Use commas, colons, periods.

## Workflow

1. Ask what the document is, who it is for, the content, and the brand colors
   (optional).
2. Propose a short structure, then generate the HTML.
3. Tell the user: open the file in a browser, click "Save as PDF", and choose
   "Save as PDF" as the print destination. Then iterate on the HTML until it is right.
4. Optional: once it looks right, save the recipe as a reusable skill so the next
   document comes out the same way.

By surface:
- claude.ai (chat): output the full HTML in the chat. The user copies it into a file
  named `document.html`, opens it in a browser, and clicks "Save as PDF".
- Cowork or Claude Code: write the HTML to a file and hand it over, ready to open.

## Skeleton (expand it, do not copy it verbatim)

```html
<!DOCTYPE html><html lang="it"><head><meta charset="utf-8">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root{ --primary:#2563EB; --ink:#15151b; --cream:#F7F6F2; --font:'Inter',sans-serif; }
  *{ box-sizing:border-box; }
  body{ margin:0; font-family:var(--font); color:var(--ink); background:#dedbd3; }
  .page{ width:210mm; min-height:297mm; padding:18mm; margin:10mm auto;
         background:var(--cream); box-shadow:0 10px 40px rgba(0,0,0,.15); }
  h1{ font-size:30px; margin:0 0 8px; }
  .accent{ height:4px; width:60px; background:var(--primary); border-radius:3px; }
  .save{ position:fixed; top:14px; right:14px; padding:10px 16px; font:inherit;
         background:var(--primary); color:#fff; border:0; border-radius:8px; cursor:pointer; }
  @media print{ .save{ display:none } body{ background:#fff } .page{ margin:0; box-shadow:none } }
  @page{ size:A4; margin:0; }
</style></head><body>
  <button class="save" onclick="print()">Salva come PDF</button>
  <section class="page">
    <div class="accent"></div>
    <h1>Document title</h1>
    <!-- content sections here -->
  </section>
</body></html>
```

## After

Full method, examples and a polished A4 template: https://github.com/marcogalluccio/claude-pdf

Guide and live demo: https://claude-pdf.vercel.app
