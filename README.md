# Letterhead

A quote or an invoice on the 19h47 letterhead, edited in place on an A4 sheet and saved as a PDF. One page, no backend, nothing to install.

## Use

1. Open `index.html` in Chrome. A double click is enough: it works from `file://`.
2. Pick the document, quote (Devis) or invoice (Facture), and its date in the pills. Write in place on the sheet.
3. Save it as a PDF with ⎙ or ⌘P, without the headers and footers of the browser. The PDF is named after the date, and the number for an invoice: `2026-10-19-2026019.pdf`.

## Print and several pages

A long document goes on over as many pages as it needs. On each page:

- The margins of the template, 98 pt at the top and the bottom and 52.64 pt on the sides, come from `@page`, not from the sheet, so a new page starts at the same height as the first.
- The footer, `19h47.fr` on the left and the reference on the right, is printed in the margin boxes `@bottom-left` and `@bottom-right` of `@page`, at the bottom of every page, whatever the length of the content. The reference is the custom property `--letterhead-ref`, a CSS string that the script writes on `<html>` with the footer of the sheet: one value for the screen and the print.
- The header of the table, Description, Quantité, Prix, Total, comes back at the top. A line is never split between two pages. The totals and the place come once, at the end.

**Chrome or Edge 131 or later only.** The page-margin boxes of `@page` are not in Firefox nor Safari: there the PDF has no footer at all. On screen the sheet stays one long page, its footer at the end.

## Features

- **Quote or invoice** — An invoice adds its number and « Fait à ».
- **Description** — An optional paragraph under the title, to set out the context of the document. « + Description » adds it; emptied, it gives way to the button again and is not printed.
- **Lines** — A title, an optional detail, a quantity in days and a unit price; the total of each line, the total before tax, the VAT and the total with tax, rounded to the cent. On screen only, each quantity shows its hours, at 8 hours a day.
- **Saved as you type** — In localStorage. « + » empties the document for a new one, keeping the issuer, the VAT number, the place and the rate.
- **Import / export** — The document as JSON, named like the PDF.
- **Grid** — G or # shows the grid of the template: 12 columns of 28 pt, 14 pt gutters, a baseline every 14 pt.
- **Light / dark theme** — Follows the system until you choose. The sheet stays white paper. The favicon follows the theme.

## Tech

- `index.html` holds the JavaScript and the styles of its own, `app-style.css` the base styles shared by the small apps, copied from [its gist](https://gist.github.com/19h47/27df983fac74beb8d3e0a30688654498) with the revision in its header. No framework, no build step.
- The sizes come from the InDesign template: Work Sans 12 pt on a 14 pt baseline grid.
- The favicon is the `description` icon of [Material Symbols](https://github.com/google/material-design-icons), by Google, under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
