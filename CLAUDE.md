# Polysome AUC Viewer — notes for Claude Code

- The entire tool is `index.html` (HTML + CSS + JS, no build step, no dependencies,
  no CDN). GitHub Pages serves `main` directly at
  https://bernhard-buss.github.io/polysome-auc-viewer/ — every push to `main` is live
  within about a minute, so keep `main` working.
- Test hook: `window.__pav` exposes `addFileText(text, name)`, `setBounds(m1, m2, p3, h, t0)`,
  `results()`, `traces()`, `landmarks()`, `autoBounds()`, `setBlank(i)`, `sensitivity()`,
  `contrastTable()`, `scalePairs()`, `tidyCsv()`, `settingsHash()`, `buildXlsx()`,
  `regionCuts()`, `regionSet()`, `regionContrasts()`, `regCols(row)` for driving the page from the
  Browser pane.
- Pipeline order matters: blank subtraction -> Hampel despike -> Savitzky-Golay (landmarks
  only) -> landmarks (incl. ladder valley depths) -> alignment (80S at 32.0 mm) -> consensus
  -> auto boundaries -> region cuts (regionCuts/regionSet: valley if median depth >= CUT_DEPTH,
  else apex midpoint; tail from the heavy boundary); integration always on the unsmoothed
  series. Region contrasts perturb the cuts by CUT_SHIFT through computeResults({cuts}). The Excel writer is hand-rolled OOXML; validate exported
  workbooks with openpyxl after changing it.
- Never add data files here. Real instrument traces used for testing live outside
  this repository (a private sibling project); serve them locally instead.
- `VERSION` (top of the script) must be bumped, with a CHANGELOG.md entry, for every change
  that alters computed numbers; leave it alone for documentation/layout/export-format work.
- CHANGELOG.md is ordered newest version first (the Changelog help tab renders it as is).
