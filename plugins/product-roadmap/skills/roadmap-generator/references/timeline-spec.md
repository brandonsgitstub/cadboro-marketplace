# Timeline Spec — Optional .xlsx Swimlane

Generate this only when the PM wants a visual or date-anchored roadmap to share. Read `/mnt/skills/public/xlsx/SKILL.md` before building. Use openpyxl.

The format is a swimlane grid: rows are lanes (themes or teams), columns are horizons (Now/Next/Later) or time periods (quarters), and each cell holds the initiatives that fall in that lane and horizon.

---

## Layout

**Sheet 1: Roadmap Timeline**

| | Now | Next | Later |
|----------------|------------------|------------------|------------------|
| **Activation** | [initiatives]    | [initiatives]    | [initiatives]    |
| **Enterprise** | [initiatives]    | [initiatives]    | [initiatives]    |
| **Reliability**| [initiatives]    | [initiatives]    | [initiatives]    |

- Column A: lane labels (themes or teams), bold, wider column (~24).
- Columns B+: horizons or quarters. If quarterly, label `Q3 2026`, `Q4 2026`, etc.
- Cells: initiative names, one per line within the cell (wrap text on). Keep names short; detail lives in the .md.
- Top-left cell (A1): the roadmap goal, or leave blank and put the goal in a merged title row above the grid.

**Title row:** merge across the top, include the product/team name and the goal the roadmap serves.

---

## Formatting

- **Color-code by horizon** to make the time gradient readable at a glance:
  - Now — solid fill, strong color (e.g., a confident green or blue).
  - Next — lighter fill of the same or an adjacent hue.
  - Later — lightest / muted fill.
  - Keep it to one coherent palette; avoid a confetti of unrelated colors.
- Header row and lane column: bold, with a subtle fill to separate them from the body.
- Borders: thin grid borders on all cells so lanes read cleanly.
- Wrap text in initiative cells; set a generous row height so multi-initiative cells aren't clipped.
- Freeze the top row and first column so labels stay visible when scrolling.

**Sheet 2 (optional): Legend & Notes** — a small reference explaining the horizon colors and listing any dependencies or assumptions that don't fit on the grid.

---

## Principle

The spreadsheet is a *visual* — its job is to make the shape of the plan obvious in one glance. Resist the urge to cram rationale into cells; the markdown roadmap carries the reasoning. If a cell needs a paragraph, that paragraph belongs in the .md, not the grid.
